## Iterables

with iter\(object\) methods

* str, list, tuple, set, dict, range
* \_\_\__iter_\_\_\(\): returns an iterable\_
* \_\__next_\_\_\(\): returns next of iterator\_

**yield**

* will return a generate in a function

#### Generators

* a special type of iterable
* concise way to construct new iterable object \(e.g. iter\(&lt;dict&gt;\)
* use **yield** instead of return
* ```py
  gen = (x ** 2 for x in range(100))
  def _make_gen():
      for x in range(100):
          yield x ** 2
  gen = _make_gen()

  def squares(n=10):
  for i in range(1, n+1)
  yield i ** 2
  gen = squares(100)
  # gen is a generator object
  for i in gen:
  print(i)
  ```
* next\(\) method to iterate through generators
* yield from to connect to generators
* send\(\) method to send values to generators

## Variable Compare and Copy

## Functional Programming in Python

Functional Programming is treating function like an object/data, a function has

* data type: form domain to range
* definition
* name/ address

In Python, the Function is a first-calss** object**. Some related usage:

* Lambda Function
  * **lambda**: x, ... : 
* decoration
* **Partial Argument Application \(closure\)**
  * functools.partial\(&lt;func\_name&gt;,&lt;parameter to fix&gt;\(list of dictionary\)\)
* lamda y: f\(5,y\) -&gt; 5 fixed
* map\( &lt;func\lambda&gt;, &lt;container&gt;\)
  * apply every function to a container
* filter\(&lt;func&gt;,&lt;container&gt;\)
* reduce\(&lt;func&gt;,&lt;container&gt;\) \(from **functools**\)

---

# Testing

### Unit Tests

### Document Tests

---

# Coding Styles

[Zen of Python](https://www.python.org/dev/peps/pep-0020/)

[PEP8 Coding Style Guid for Python](https://www.python.org/dev/peps/pep-0008/)

[Google Python Coding Style](http://google.github.io/styleguide/pyguide.html)

* reloading module dependencies
  * use import lib module
    * importlib.reload\(&lt;lib&gt;\)
  * IPython can do dreload
    * deep reload
* keep objects and data alive in _if \_\_name\_\_ == '\_\_main\_\_' \_block
  * everything you want to expose by %run
* flat better than nexted
  * longer files, less jumping around files
    * special about python



