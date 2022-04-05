# Python built-in types

- [Python built-in types](#python-built-in-types)
  - [Sequence Types](#sequence-types)
    - [Common Operations](#common-operations)
    - [Methods of sequences](#methods-of-sequences)
      - [private methods](#private-methods)
    - [**str**](#str)
    - [**List**](#list)
    - [Set and Frozen Set](#set-and-frozen-set)


Most Data Types are [Implemented in C](https://github.com/python/cpython/tree/949fe976d5c62ae63ed505ecf729f815d0baccfc)

* Almost anything \(function and data\) in Python is an object \(all things in HEAP\)
  * id\(\)
  * bool, float, int\(usually long or long long\)
* common used functions for numerical
  * abs\(\),round\(\),divmod\(\),pow\(\)
  * float\(\),int\(\),str\(\),bool\(\), hex\(\),oct\(\)
  * chr\(\),ord\(\)
* complex
  * .real, .img
  * a + bj
* str\(\), type\(\) applies to all
* range\(\) : returns a range object \( a generator-like object by lazy valuation\) \(xrange is deprecated in Python3\)

---

## Sequence Types

### Common Operations

Standard Operators

* ==, &gt; , &lt; , &gt;=, !=compare values
* is, is not identity
* and or --boolean operation \(cut automatically\)

Sequence Operators

* **a\[ind\], a\[i:j\], a\[start:end:step\] **- slice notation
* a\[:\] - **a copy**
* count from i, to j, distance k \(all can be default\)
* a\*b - repeat b times
* a+b, += append
* a in b - judge if a is in b

### Methods of sequences

* max\(\), min\(\), sum\(\), len\(\)
* enumerate\(\)\(key-value pairs\), 
* sort\(\), reverse\(\)
* **reversed\(\),** sorted\(&lt;val&gt;, \[key\], \[reverse\] \), - use to loop
* **zip\(&lt;seq1&gt;, &lt;seq2&gt;\)**
  * seq1, seq2 = zip\(\*zipped\) - unzip things
* del &lt;ele&gt;: delete on element from sequence

#### private methods

a.

* _\_\_sizeof\_\_\(\)\_
  * show storage

---

### **str**

* **immutable**
  * += is exception, will modify the object
  * any modification is done by creating a new string
    * exception: some methods can modify the string for performance reason
* single, double, triple quotes
* r "&lt;str&gt;" : raw string : disable escape characters
  * use in error handling/debug
* escape characters
  * \newlinem \n, \t, \b, \v
  * \0, \a, , \"...
* **format string**
  * use {} and .format
  * position\[Name\]: \[Alignment\]\[sign\]\[minimum width\]\[.precision\]\[type\]
  * +m.nf: output with sign, keep n digits, length m
  * &lt;&gt;:alignment, ^ center
  * type specifier; s-str, b- binar, p-octal, x-hex, d-integer, c-char, f-fixed point\(default precision6\), e-exponent notation\(default precision 6\)
* **Methods** for String - some methods will work as mutation of the string
  * +, += 
  * find\(\), rfind\(\),index\(\), rindex\(\)
  * isupper\(\), islower\(\), upper\(\), lower\(\), capitalize\(\)
  * center\(\), count\(&lt;pattern&gt;\), encode\(\)
  * **join\(\)**,
  * strip\(\), replace\(\), split\(\), translate\(\), startswith\(\), endswith\(\)
  * lstrip\(\), rstrip\(\), split\(\)
  * translate\(\) needs the method of maketrans\(\)
  * zfill\(\)
  * format\(&lt;data&gt;\) - format string syntax
  * ord\(&lt;char&gt;\) - get ASCII Code
  * char\(&lt;double&gt;\) - to convert to array
  * ljust, rjust - justify, padding with whitespace

---

### **List**

* mutable type
* Anything can be put in ONE List
* different types
* dynamic array 
* when usage reaches 80%, double storage when call append
* Methods of list
  * append\(\)
  * extend\(\) - append multiple elements
  * lst\[len\(lst\):\]=\[x\] 
  * extend\(\), insert\(&lt;idx&gt;, &lt;val&gt;\),remove\(&lt;val&gt;\), reverse\(\), copy\(\) sort\(\),count\(\), 
  * pop\(\)
  * index\(\) - find method
  * count\(\) 

**List Comprehension** -achieved by generator

* ```py
  doubled_odds = [n * 2 for n in numbers if n % 2 == 1]
  flattened = [n for n in row for row in matrix]
  {value: key for key, value in original.items()}
  ```

**Implementation**

* over allocated array in C
  * allocated &gt;= len\(list\) = ob\_size

---

### **Tuple**

* Immutable
  * fixed \(allocated\) array in C
* Usage: key in mapping type, special parameter for function, special **return value** for function\(multiple returns\)
* pakcing and unpacking 
  * a,b,c = &lt;tuple&gt;
  * a,b, \(c,d\) = &lt;tuple&gt;
  * a, b, \*rest = &lt;tuple&gt;
* plucking

Performance of Tuple: Performance of tuple would be faster than list. Python would cache some of the tuple allocated so when creating a tuple with similar size, the performance would be optimized.

---

### Dictionary

* Key, value, and key-value pairs
  * key by hash\(&lt;key&gt;\) - must be hashable type
  * **list** is unhashable
* Creation: 
  * dict\[key-value tuples\], dict\(key0=val0,key1=val1,...\)
  * {}.fromkeys\(key-tuple, init\_val\)
  * dict\(zip\(key,val\)\)
* Operations
  * a\['key1'\] 
* Methods
  * A in B - operator 
  * .keys\(\), values\(\)
  * **items\(\)**-returns \(key,value\) tuples
  * A.update\(b\) - update b info to A
  * .get\(&lt;key&gt;, \[default value\]\)
  * pop\(\), clear\(\)
  * popitem\(\)
    * last=True: default to pop the lasted inserted item \(stack\)
    * returns \(key, val\) as tuple
  * setdefault\(&lt;key&gt;, \[default = None\]\)
    * returns the key's value, if not, set key to default value and return key
  * clear\(\) - remove all items

#### Implementation of dictionary

for python 3.7+, dictionary becomes ordered type. The storage of index and hash table is separated to optimize space usage.

When hash collision happens, hash\(key\) and mask = PyDicMinSize - 1 \(use & operation\) doesn't match. The insertion is optimized.

```py
Indices
----------------------------------------------------
None | index | None | None | index | None | index ...
----------------------------------------------------


Entries
--------------------
hash0   key0  value0
---------------------
hash1   key1  value1
---------------------
hash2   key2  value2
---------------------
        ...
---------------------
```

---

### Set and Frozen Set

* set-variable set, frozenset-fixed set
* Creation-set\(&lt;list or tuple&gt;\)
  * no repetitive data types
  * strings will be set of chars
* Operations
  * in, not in \(val in s\)
  * ==, !=
  * &lt; \($$\subset$$\), &lt;=,  &gt;, &gt;=
  * &, \|, - or \\(or\), ^\($$\Delta$$\)
* Methods-ALL SETS
  * .issubset\(\), isupperset\(\)
  * union\(\),intersection\(\),difference\(\),symmetric\_difference\(&lt;b&gt;\)
  * copy\(\)
* Methods-Variable sets only
  * add\(\)
  * update\(t\), intersection\_update\(t\), \_difference\_update\(t\), \_symmetric\_difference\_update\(t\)
    * \|=， &=， -=， ^= 
  * remove\(obj\),discard\(obj\) - remove
  * remove will fail
  * pop\(\), clear\(\)
  * enumerate\(\) - returns value: count pair





