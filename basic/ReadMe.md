# Basic Grammars

* Indentation Language, "/" to change line \(or use\(\),""\)
* comment \#
* initializing and assignment \(by tuples\) and variable scope
* ```py
  a, b , c = 'hi', 1, 3.0 # comment
  f=g=10 # chained assignment
  def f(x):
      global d # global variable
      e = 4 # local variable 
      print(a)
  ```
* all variables assigned by **reference**
  * ```py
    [[0] * 2 for _ in range(2)] != [[0]*2]*2
    # assign by tuples
    a, b = 1, 2
    ```
* support +=, ^=, &lt;&lt;= ...
* [keywords](https://docs.python.org/3/reference/lexical_analysis.html#keywords): notations cannot used by other objectes
* Expressions

### Operations

* // for integer \(floor\) divide
* divmod\(\) - get remainders
* is, is not: compare id
* and, or, not: boolean
  * Semantic Sugar
* * ```py
    [] or [None] # returns [None]
    [] or [1,2] # return [1,2]
    [1,2[] or [3,4] # return [1,2]
    ```
* % for remainder
* \*\* for exponential \(^\)
* &lt;operator&gt;= supported in most cases
* **math** library
* logical operators: not, and, or 
* bitwise operators: &gt;&gt;, &lt;&lt;, ^, &, \|, ~
* ```py
  1 > 2 > 3 # true
  ```

### Control Structures

* if then elif else
* for loop - for \( \*iter\(s\) in container\):
  * break, continue
  * for with else
  * ```py
    for n in range(2, 10):
        for x in range(2, n):
            if n % x == 0:
                print( n, 'equals', x, '*', n/x)
                break
        else:
            # loop fell through without finding a factor
            print(n, 'is a prime number')
    ```
  * _ternary expression: &lt;true-expr&gt; if true else &lt;false-expr&gt;_
* while 
* try: except:
* pass : no operation

### Environmental Variables

* If \_\_name\_\_ == "main":
  * when the module \(py file\) is called directly via interpreter, this will be named main
  * if imported elsewhere the variable is different 

### Constant

* Constant usually defined as module level , named with CAPITAL LETTERS and underscores

### Variable Lifetime and Variable Scope

* variable scope and lifetime is from declaration to program end
* scope is covered inside a loop/conditional statement
* global variable
  * \_global \_keyword
  * can modify mutable global variable in function
  * cannot modify immutable global variable \(eg. += \) in a function without "global"
* nonlocal variable
  * _nonlocal_ keyword
  * similar to global, used for outer scope variable

---

## Import Libraries

**module and package**

* a Module is a file containing Python code
* a package is a hierarchically structured collection of related modules
* _\_\_\_name\_\_\_ is a set to the name of the module\_
  * the interactive shell has the name "_\_\_\_main\_\_\_"\_

```
mycompany
 ├─ web
 │  ├─ __init__.py
 │  ├─ utils.py
 │  └─ www.py
 ├─ __init__.py
 ├─ abc.py
 └─ utils.py
```

* from &lt;lib&gt; import &lt;func&gt;
* import &lt;lib&gt; \(as...\)  then specify the full name of the operation\(&lt;lib&gt;.operation in your code\)
* from &lt;lib&gt; import \* \(import all\) - NOT RECOMMENDED will cover your own variables maybe

## 



