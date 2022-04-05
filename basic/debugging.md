## Error Handling and Exception

* exception classes: 
* BaseException\(base class\), 
  * Exception, 
  * AttributeError, IndexError,
  * IOError, KeyboardInterrupt, 
  * KeyError, 
  * NameError
  * SyntaxError
  * TypeError
  * ValueError
* ```py
  try:
      expressions
  except (ValueError, Index Error) as err: # can be any exception class, as err is optional (to catch the error)
      print(err)
  except Exception as err:
      print("general exception" # handle all exception types
  else:
      print("\n")
  finally:
      print("final clause")  # finally will always be executed

  # notice:
  # variable "err" will be deleted after the try block
  ```
* finally block will always be executed
* user can define error types
* ```py
  class MyInputError(Exception):
      """Exception raised when there're errors in input"""
      def __init__(self, value): 
          self.value = value
      def __str__(self):
          return ("{} is invalid input".format(repr(self.value)))

  try:
      raise MyInputError(1) # Throw
  except MyInputError as err:
      print('error: {}'.format(err)
  ```
* throw error by **raise\(\)**
* ```py
  # err_reraise.py

  def foo(s):
      n = int(s)
      if n==0:
          raise ValueError('invalid value: %s' % s)
      return 10 / n

  def bar():
      try:
          foo('0')
      except ValueError as e:
          print('ValueError!')
          raise

  bar()
  ```
* **assert **
  * throw AssertionError
* logging use the logging module

#### pdb

[pdb](https://docs.python.org/3/library/pdb.html) commands

* Single Step run
  * ```
    $ python -m pdb err.py
    ```
* Set Trace

  * ```
    import pdb

    pdb.set_trace() # will stop here
    ```

* [debugger commands](https://docs.python.org/2.0/lib/debugger-commands.html)

## Profiling

#### cProfile 

[profilers in python](https://docs.python.org/2/library/profile.html)

python -m cProfile &lt;file&gt;

#### line\_profiler

[line\_profiler](https://github.com/rkern/line_profiler)

[magic commands](https://web.archive.org/web/20140513005858im_/http://www.appneta.com/blog/line-profiler-python/)

### Modules

#### Logging

logging to log error \(or info\) messages to files and check

#### 



