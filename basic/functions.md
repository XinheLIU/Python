### Functions

#### Built-in Functions

* dir\(\_\_builtins\_\_ \)
* common useful functions
  * dir\(\), help\(0
  * id\(\)
  * exists\(\)
    * object, variable exist or not
  * range\(\),len\(\)
  * open\(\)
  * max\(sequence, \[key\]\), min\(\)

#### User Defined Functions

* def\( \*args, \*\*kargs\)
  * key word parameters
  * support "named parameters\(kargs\)
  * \*stands for an arbitrary number,\* also pack variables as a tuple \(can use \* to pack\)
  * return multiple values by returning a tuple
  * type hints and type aliases \(Vector = List\[float\]\)
* ```py
  def greeting(name: str) -> str:
      return 'Hello ' + name
  greeting('Charles')
  ```
* function has a name, can compare by environmental variable
  * if \_\__name\_\_ = funcname:\(\)\_
* when the main function calls the function, **must be after the definition**
  * when other functions calls it, need not to be defined before

##### function can be **nested** \(define function within another function\)

* inside function is encapsulated, not accessible in global scope
* **closure** - function returns another function, often used together with decorator

  * ```py
    def nth_power(exponent):
        def exponent_of(base):
            return base ** exponent
        return exponent_of 

    square = nth_power(2) 
    cube = nth_power(3)  
    square
    # output
    <function __main__.nth_power.<locals>.exponent(base)>

    cube
    # output
    <function __main__.nth_power.<locals>.exponent(base)>

    print(square(2)) 
    print(cube(2)) 
    # output
    4 # 2^2
    8 # 2^3
    ```

##### call by **neither value, nor reference - passed by assigment/object reference**

* variables are assigned by "binding name to values", when a=b, a,b are bind into same value
* name \(reference\) in stack, object in heap
* when change a to a = val, a is bind to a different value and id\(storage place\)
* when pass as an argument
  * **re-assign** will not change the object \(create a new object instead\)
  * **modify** will affect the object

##### function usually has no side effects \( change only **return value\)**

* in functional programming \(all passed by value, not mutable when** re-asign, modify**\)
* function can have side effects by changing \(eg. += \) **mutable **types \(eg. list\) in function
* immutable type cannot be changed

##### variable is **dynamically typed**

* python 3 has type hint

##### Variable Scope

* **global **key word 
  * indicates this is a varaible out of local scope
  * cannot **modify **global variables value inside a local function
* **nonlocal **keyword
  * indicates this is a variable from outside scope in **nested** functions

##### Lambda

unamed functions

* **lambda **&lt;parameters&gt;: &lt;expression&gt;
  * lambda is an expression not a statement

### Input/output

* input\(&lt;prompt&gt;\) function
  * raw\_input\(&lt;prompt&gt;\) in Python2
  * is a **string**, use int\(\), float\(\) to cast
* **print** variable holder in {}: 
  * print\("hello, {}", format\(s\) \) or print\("hello, {s}"\)
  * Use format string \(see **string**\)
  * line change : add argument end = " ", no change: end = ' '
* get command-line input/output : 
  * **sys** library: sys.argc, sys.argv

### Module, Package, Library

* A complete file is a module
  * from module import ... \( \* can be a wildcard -everything \)
  * import module \[as ...\]
  * module functions can be assigned to variables
* A hierarchical file directory structure is a package
  * defines the execution environment for Python applications \(consisting of submodules and sub-packages\)
  * Library is a collection of modules with related functions



