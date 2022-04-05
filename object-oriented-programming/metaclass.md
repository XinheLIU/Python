# MetaClass

### Type

* return the type of the class
  * instance type is the class
  * class is of type 'type'
    * class is an instance of 'type'
* can **dynamically create new types without definition**
  * ```py
    >>> def fn(self, name='world'): # member function
    ...     print('Hello, %s.' % name)
    ...
    >>> Hello = type('Hello', (object,), dict(hello=fn)) # create hello calss with attribute hello
    ```

### Metaclass

* inherit type
  * template \(parent\) of classes
* allows you to create and modify classes
  * and modify the behaviors in class creation 
* class is the instance of metaclass
* overwrites \_\__new_\_\_ to modify class creation behaviors
  * the _type.\__\_new\_\_\(class, name, bases, attrs\) \_is called when python interpretor **finds class definitions**

### MetaClass in Engineering

### Example

ORM\(Object-Relational Mapping\)

```py
# use case
class User(Model):
    # class attributes to columns：
    id = IntegerField('id')
    name = StringField('username')
    email = StringField('email')
    password = StringField('password')

# create instance
u = User(id=12345, name='Michael', email='test@orm.org', password='my-pwd')
# save
u.save()
```

```py
class Field(object):

    def __init__(self, name, column_type):
        self.name = name
        self.column_type = column_type

    def __str__(self):
        return '<%s:%s>' % (self.__class__.__name__, self.name)

class StringField(Field):

    def __init__(self, name):
        super(StringField, self).__init__(name, 'varchar(100)')

class IntegerField(Field):

    def __init__(self, name):
        super(IntegerField, self).__init__(name, 'bigint')

class ModelMetaclass(type):

    def __new__(cls, name, bases, attrs):
        if name=='Model':
            return type.__new__(cls, name, bases, attrs)
        print('Found model: %s' % name)
        mappings = dict()
        for k, v in attrs.items():
            if isinstance(v, Field):
                print('Found mapping: %s ==> %s' % (k, v))
                mappings[k] = v
        for k in mappings.keys():
            attrs.pop(k)
        attrs['__mappings__'] = mappings # save mapping
        attrs['__table__'] = name # table name and column name - same
        return type.__new__(cls, name, bases, attrs)

lass Model(dict, metaclass=ModelMetaclass):

    def __init__(self, **kw):
        super(Model, self).__init__(**kw)

    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttributeError(r"'Model' object has no attribute '%s'" % key)

    def __setattr__(self, key, value):
        self[key] = value

    def save(self):
        fields = []
        params = []
        args = []
        for k, v in self.__mappings__.items():
            fields.append(v.name)
            params.append('?')
            args.append(getattr(self, k, None))
        sql = 'insert into %s (%s) values (%s)' % (self.__table__, ','.join(fields), ','.join(params))
        print('SQL: %s' % sql)
        print('ARGS: %s' % str(args))
```



