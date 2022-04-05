## Sequence Comprehension

* shortened for loop
* \[\[lambda\]\(x\) for x in &lt;collection&gt;\] for y in &lt;collection&gt;\]
* \[ ... for \(k,v\) in dict\]

## Decorator

function as an argument of another function 

Example

```py
def log(text):
    def decorator(func):
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator
    
@log('execute')
def now():
    print('2015-3-25')
```

* the _\_\_name\(\)\_\_ _attribute will be changed after the decoration \(to "wrapper"\) 
  * use functools.wrap 

```py
import functools

def log(func):
    @functools.wraps(func)
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper

def log(text):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator
```



