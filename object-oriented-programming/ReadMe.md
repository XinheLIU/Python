# Python Class

### Class Definition

* class &lt;name&gt;\(&lt;parents&gt;\): the common 'Object' as a parent
  * **static member variables/class attributes **- just state outside constructor 
  * instance member varaibles/attributes
    * with same name, instance member will shadow the class membera
    * ```py
      >>> class Student(object):
      ...     name = 'Student'
      ...
      >>> s = Student() 
      >>> print(s.name) 
      Student
      ```
* def \_\_init\_\_\(self, vars\): \_constructor
* private members: default is **public**
  * **double underline** \_\_ 
    * indication for private variable
    * \_var will be replaced by** \_classname\_\_var**, preventing conflict of same name in base and derived class
  * single underline \_
    * to prevent attributes be loaded by "**from module import**"
* def name\(self, vars\): **member functions**
  * usually modify the class \(self\)
* class member function - the** class method: @classmethod decorator**
  * the member function does not modify self
* **static member function**: **@staticmethod** decorator
* operator overload
  * \_\_eq\_\_\_

### Property and Setter

@property and @&lt;attribute&gt;.setter decorates the function to be getter and setter

### Inheritance

* must call parent constructor in **init\(\)** explicitly
  * child constructor -&gt; parent contructor
* Support** multiple inheritance**
  * isinstance\(A,B\) - is A an Instance of B
  * use **super\(\)** to avoid multiple constructor call
    * if needs to call multiple constructors, must use _parent._\_init\_\_\(\) method to explicitly call the second parent
    * use [C3 linearization](https://en.wikipedia.org/wiki/C3_linearization) for method resolution
  * **MixIn**
    * achieve different functions through multiple inheritance
* Abstract method: **@abstractmethod** decorator

### Methods on classes

* isinstance\(a, class name\)
  * judge inheritance 
* type\(\)
  * class type
  * **types** module
    * include function types, generation types, etc
* dir\(\)
  * show all attributes and methods
* getattr\(&lt;obj&gt;, str\), setattr\(\), hasattr\(\)
  * throw AttributeError is not found

### Dynamic Programming Language

vs Java\(static language\)

* object shares same **methods** will be treated likely
* bind attributes and methods to instances freely

  * ```py
    class Student(object):
        def __init__(self, name):
            self.name = name

    s = Student('Bob')
    s.score = 90

    def set_age(self, age):
        self.age = age
    from types import MethodType
    s.set_age = MethodType(set_age, s)
    ```

* **\_\_**_**slots**_**\_\_**: **special variable **to define the list of attributes we allow to bind

  * **does not** work on children

* * ```py
    class Student(object):
        __slots__ = ('name', 'age')
    ```

### customized class methods

* \_\__str_\_\_
  * use by print\(\)
* _\_\_repr\_\_\_
  * used by call func name, usually can be the same as above
* \_\__len\_\_\_
* \_\__iter\_\_ and \_\_next\_\_\_

  * used by for ... in
  * will call _\_\_next\_\_\(\)\_ to get next one
  * ```py
    class Fib(object):
        def __init__(self):
            self.a, self.b = 0, 1 

        def __iter__(self):
            return self 

        def __next__(self):
            self.a, self.b = self.b, self.a + self.b # 计算下一个值
            if self.a > 100000: 
                raise StopIteration()
            return self.a
    ```

* \_\__getitem\_\_\_

  * supports random access \(list-like object\)
  * usually needs to support** int** or **slice **type of inputs

* _\_\_getattr\_\_\(self, attr\)\_

  * the way python gets attributes
  * can be over-written to suppress attribute errors of parse commands
  * ```py
    class Chain(object):

        def __init__(self, path=''):
            self._path = path

        def __getattr__(self, path):
            return Chain('%s/%s' % (self._path, path))

        def __str__(self):
            return self._path

        __repr__ = __str__
    ```

* \_\__call\_\_\_\(self\)\_

  * directly calls the object instance
  * ```py
    class Student(object):
        def __init__(self, name):
            self.name = name

        def __call__(self):
            print('My name is %s.' % self.name)

    >>> s = Student('Michael')
    >>> s()
    My name is Michael.
    ```
  * callable\(&lt;object&gt;\)
    * if a object is a **Callable**

### Examples

```py
class Document():
    # static variable/constant
    WELCOME_STR = 'Welcome! The context for this book is {}.'

    def __init__(self, title, author, context):
        print('init function called')
        self.title = title
        self.author = author
        self.__context = context

    # class method
    @classmethod
    def create_empty_book(cls, title, author):
        return cls(title=title, author=author, context='nothing')

    # member function
    def get_context_length(self):
        return len(self.__context)

    # static function
    @staticmethod
    def get_welcome(context):
        return Document.WELCOME_STR.format(context)


empty_book = Document.create_empty_book('What Every Man Thinks About Apart from Sex', 'Professor Sheridan Simove')


print(empty_book.get_context_length())
print(empty_book.get_welcome('indeed nothing'))

########## output ##########

init function called
7
Welcome! The context for this book is indeed nothing.
```

```py
from abc import ABCMeta, abstractmethod

class Entity(metaclass=ABCMeta):
    def __init__(self, object_type):
        print('parent class init called')
        self.object_type = object_type

    def get_context_length(self):
        raise Exception('get_context_length not implemented')
    @abstractmethod 
    def get_title(self): 
        pass

class Document(Entity):
    def __init__(self, title, author, context):
        print('Document class init called')
        Entity.__init__(self, 'document')
        self.title = title
        self.author = author
        self.__context = context

    def get_context_length(self):
        return len(self.__context)

class Video(Entity):
    def __init__(self, title, author, video_length):
        print('Video class init called')
        Entity.__init__(self, 'video')
        self.title = title
        self.author = author
        self.__video_length = video_length

    def get_context_length(self):
        return self.__video_length

harry_potter_book = Document('Harry Potter(Book)', 'J. K. Rowling', '... Forever Do not believe any thing is capable of thinking independently ...')
harry_potter_movie = Video('Harry Potter(Movie)', 'J. K. Rowling', 120)

print(harry_potter_book.object_type)
print(harry_potter_movie.object_type)

harry_potter_book.print_title()
harry_potter_movie.print_title()

print(harry_potter_book.get_context_length())
print(harry_potter_movie.get_context_length())

########## output ##########

Document class init called
parent class init called
Video class init called
parent class init called
document
video
Harry Potter(Book)
Harry Potter(Movie)
77
120
```

---

# Python Modularization

Some principles

* import once
  * usually at the beginning of program
* use absolute file path
  * don't use sys.path.append\(\) to change running path
* Single Repository
  * [Why Google uses a single repo](https://cacm.acm.org/magazines/2016/7/204032-why-google-stores-billions-of-lines-of-code-in-a-single-repository/fulltext)
  * simplify dependency management
* Set up independent running environments

  * two ways to change running path \(the list interpretor looks for packges\)

    * ```py
      import sys  

      print(sys.path)

      ########## output ##########

      ['', '/usr/lib/python36.zip', '/usr/lib/python3.6', '/usr/lib/python3.6/lib-dynload', '/usr/local/lib/python3.6/dist-packages', '/usr/lib/python3/dist-packages']

      # change path
      sys.path[0] = '/home/ubuntu/workspace/your_projects'
      ```
    * ```py
      # use Virtual Enviornment
      # in the activate file in the virtual environment
      export PYTHONPATH="/home/ubuntu/workspace/your_projects"
      ```
    * use the second one

* If need running code in package \(eg. printing\) use _if \_\_name\_\_ == '\_\_main\_\_'



