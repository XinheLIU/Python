### File

* f\_obj = open\(&lt;filename&gt;, mode='r',buffering=-1,...\): a file object 
  * mode: 
    * r=read,
    * w=write
    * a=appending
    * x=exclusive crate\(fail if already exist\)
    * b=binary mode
    * +=open a disk file for updating\(read+write, eg. r+ or a+\)
    * t=text mode\(default\)
  * buffering: 0=off, 1=line buffering, &gt;1 indicate the size in bytes a fixed-size chunk-buffer
  * iterative 
  * methods
    * .read\(\[size\]\), .readline\(\), .readlines\(\)
    * .write\(\), .writelines\(\)
    * .close\(\)
    * .seek\(offset, whence=0\): with offset bytes from whence\(0=begin,1=current,2=end\)
      * when falls in the middle of unicode could cause error
    * truncate\(\) - erase the content of file

### Context Manager

**with** open\(&lt;path&gt;, \[mode\]\)** as** &lt;var&gt;:  with block

* automatic clean-up \(no need to close\)

* standard file: sys.stdin/stdout/stderr

* _text mode_
  * the default mode - work with file as python strings\(i.e. Unicode\)
  * UTF-8: may need to decode to str yourself
    * data.decode\('utf8'\)
  * with open\(..., encoding = 'iso-8859'\) as f:
    * from one unicode to the other unicode

with works with objects that have \_\__enter_\_\_ _and _\_\_exit\_\_ methods \(eg. the output of open\(\)\)

```py
try:
    f = open('/path/to/file', 'r')
    f.read()
finally:
    if f:
        f.close()

# is equivalent to
with open('/path/to/file', 'r') as f:
    f.read()

# context object
class Query(object):

    def __init__(self, name):
        self.name = name

    def __enter__(self):
        print('Begin')
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        if exc_type:
            print('Error')
        else:
            print('End')

    def query(self):
        print('Query info about %s...' % self.name)

with Query('Bob') as q:
    q.query()
```



