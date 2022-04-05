# N**umPy**

* Implemented in C, stores data in contiguous memory blocks
  * internal storage includes
    * pointer to data
    * data type \(dtype\), describes fixed-size value cells
      * [numpy dtype hierarchy](https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.scalars.html)
      * np.issubtype
    * tuple for array shape
    * tuple for strides: number of bytes to step 

## ndarray\(n-dimension array\)

* Data Types and **Type Code**
  * int8\(unit\) to int62\(i1, u1 to i8, u8\), float 16 to float128\(f2 to f16 \(f4=f, f8=d, f16=g\)
  * complex64\(c8 or c16\) to complex256
  * bool \(?\)
  * object\(0\) - Python object type
  * string\_ \(S\) fixed length ASCII string type \(eg. use length 10 "S10"\)
  * unicode\_ U \("U10"\)
* Attributes
  * .ndim\(rank\), shape\(dimension\),size, dtype, itemsize\(size of item\(in byte\)
* Methods
  * \[\] - indexing with m:n or** logical indexing**
    * ```py
      data[name == 'Bob', 2:] 
      #Bod could be another list with length n rows
      ```
    * fancy indexing
      * take\(&lt;ind&gt;, axis=\) and put\(&lt;ind&gt;\)
        * put uses C order
  * **shape, ndim, dtype, size **
    * dimension \(5,\) is different from \(5,1\), the former is a rank-1 array
  * reshape\(\[order='C' or 'F'\] \)
    * reshape\( n, -1\) : flatten all other dimensions \(to \(n, \(n\_2\*n\_3..\*n\_n\)\)
    * [C order \(row major\) vs Fortran order \(column major\)](https://en.wikipedia.org/wiki/Row-_and_column-major_order)
  * .ravel\(\['C' or 'F'\]\) and flatten\(\)
    * flatten return a copy
  * .T - transpose
  * copy\(\) - deep copy
  * Aggregation
    * sum\(\),mean\(\)
    * var\(\),max\(\),min\(\)
    * argmin\(\),argmax\(\)-return index
    * cumsum\(\),cumprod\(\)
    * argument: keepdims = True : to avoid rank-0 array
  * any\(\), all\(\) - works on logical nd array
  * sort\(\[axis\]\)
    * argsort\(\[kind=\]\) and lexsort\(\)
      * return sort indexers \(sort and lexical sort\)
      * kind = 'quiksort' \(default\), 'mergesort', 'heapsort'
    * np.partition\(arr, pos\), np.argpartition\(\)
    * searchsorted\(val\)
      * returns index by binary search
  * unique\(\)

## Numpy \(np.\)

#### Creation

* array\(&lt;sequence&gt;0
* asarray\(\) - covert input to array, not copy if already an np array
* arrange\(\[start,\] stop, \[step,\], dtype = None\) - like range
* linespace\(start, stop, num, endpoint...\)
* logspace\(\)
* _ones\(&lt;shape&gt;\), ones\_like\(&lt;another array of same shape&gt;\), zeros, zeros\_like_
* _empty, empty\_like, full, full\_like_
* eye\(\), identity\(\)
* fromfile\(\), fromfunction\(\)

#### Operations

* shape
* a\[a,b\] - same usage for : \(to or all\) as list
* \*+-/ - Element wise operation
  * Numpy will do "broadcasting" by copying elements \(eg. \(5,3\) array + \(5,1\) array is \(5,3\)\)
* np.squeeze - select a subset 
* concatenate and split
  * dstack\(\) - stack in 'depth' wise
  * vstack\(\) and row\_stack 
  * htack\(\) and column\_stack
    * column\_sstack converts one d array to 2d columns first
  * r\_\(\) 
    * row\_stack\(\)
  * c\_\(\)
  * split\(arr, \[...\]\), vsplit
* isnan\(\)
* np.where\(\) -selection

### Functions \(np.\) - \(**ufunc\(\)** - implemented in C usually\)

#### Looping

* wrap function using [np.vectorize ](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vectorize.html)
* **apply\_along\_axis\(&lt;lambda&gt;\)**
  * all, exp, floor, ceil, clip, conj, corrcoef, cov, bincoun\)

##### Unary

* abs, fabs
* sqrt, square 
* exp, log, log10, log2, log1p
* sign, ceil, floor
* rint
* modf - fractional and integral part
* isnan
* isfinite, isinf
* cos, sin, cosh, sinh, tan, tanh, arcsin, arccost, ...
* logical\_not

##### Binary

* add, substrct, multiply, divide, floor\_divide, dot, power
  * @ is matrix multiply \(dot\)
* maximum, fmax\(ignores NaN\), minimum, fmin
* copysign
* greater, greater\__equal, less\_euqal_
* _logical\_and, logical\_or_
* outer\(\) - [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product)

##### Multiple\(aggregators\)

* reduce

  * operations can be chained

    * ```py
      arr = np.arange(10)

      np.add.reduce(arr)
      # 45
      ```

* accumulate - \(cumulative reduce\)
* [reduceat\(](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.reduceat.html)arr, \[reduce cuts\]\)

#### Logical Indexing

np.

* unique\(x\)
* intersect1d\(x,y\)
* union1d\(x,y\)
* setdiff1d\(x,y\)
* setxor1d\(x,y\)

#### Others

* np.meshgrid\(\) -1D to 2D
* np.where\( &lt;cond&gt;, &lt;if array&gt;, &lt;else array&gt;\)
  * &lt;if array&gt;.where\(&lt;cond&gt;\)

#### Linear Algebra

* dot - matirx mutliply
* .outer\(\) - outer product
* **.linalg**
  * diag,
  * trace
  * .det, inv, solve, eig,
  * pinv - Moore-Penrose pseudo-inverse of a matrix
  * norm\( , keepdims = True\)
* np.asmatrix \(**Matrix**\)

#### Random

np. random

* seed - set seed
* RandomState\(\) - create one generator independent of others
* permutation
* shuffle
* rand, randint
* randn \(std normal\), binomial, beta, normal, chisquare, gamma, uniform
* choice\(&lt;list&gt;, size, \[prob\]\) - choose among

---

# Advanced

### Broadcasting

* [broadcasting](https://docs.scipy.org/doc/numpy-1.15.0/user/basics.broadcasting.html)
* automatic casting of smaller one to meet the shape of bigger one in linear algebra and general calculations

### Numpy File I/O

deal with either text of binary format. Arrays are saved by default in umcompressed raw binary format with file extension **.npy.** Compressed form is **.npz**

np.

* load\(&lt;npy&gt;/&lt;npz&gt;\)
  * npz returns dict-like struct \(lazily\)
* save\(\)
* savez\(&lt;file&gt;, &lt;var dict&gt;\)
  * a=..., b=///
* savez\_compressed\(&lt;file&gt;, a = arr, b = arr\)

### User-defined, C-like ufuncs, dtypes and Numba

np.

* [frompyfunc](https://docs.scipy.org/doc/numpy/reference/generated/numpy.frompyfunc.html)\(func, nin, nout\)
  * returns python objects
* [vectorize](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vectorize.html)
  * can specify output type

[Structured array](https://docs.scipy.org/doc/numpy/user/basics.rec.html)

* structured array can compress complex nested objects to single block of memory 

##### Numba

[Numba](http://numba.pydata.org/numba-doc/latest/index.html)

* njit\(\[nopython\]\)
  * indicates any python API calls
* float64

Uses [LLVM](https://llvm.org/) project to translate python code to compiled machine code

### Advanced Array Input and Output

* memmap object
  * nd-array like object, enable large file to be read and written without loading to memory
* np.memap

memmap

* flush\(\)

### Numpy Functions for Deep Learning

np.pad\(\)

### Numpy Performance Tips

* vectorize 
  * loops and condition logic to array operations and boolean operations
  * use contiguous memory \(C-contiguous\)
    * arr.flags
* broadcasting if possible
* use views to avoid copy
* Utilize ufunc

### Examples

[Examples List](http://scipy.github.io/old-wiki/pages/Numpy_Example_List)

