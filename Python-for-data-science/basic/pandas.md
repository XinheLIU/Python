# Pandas

- [Pandas](#pandas)
  - [Basic Data Structure and Creation](#basic-data-structure-and-creation)
    - [Series](#series)
    - [DataFrame](#dataframe)
    - [Index](#index)
      - [Hirerachical Index](#hirerachical-index)
  - [Data Manipulation](#data-manipulation)
    - [Data Selection : Indexing and Slicing (and Add/Modify in place)](#data-selection--indexing-and-slicing-and-addmodify-in-place)
    - [Operation on Data](#operation-on-data)
      - [Mathematical Operations](#mathematical-operations)
      - [Modify](#modify)
      - [Bining](#bining)
      - [View/ Conversion to other types](#view-conversion-to-other-types)
        - [Random Samples](#random-samples)
    - [Functions](#functions)
      - [Windows](#windows)
  - [Aggregation and Grouping](#aggregation-and-grouping)
    - [Pivot Table](#pivot-table)
    - [Pandas Sql](#pandas-sql)
      - [Combine DataSets](#combine-datasets)
  - [Data Preprocessing](#data-preprocessing)
    - [Descriptive](#descriptive)
      - [Pandas Data Profiling](#pandas-data-profiling)
    - [Reshaping](#reshaping)
    - [Duplication](#duplication)
    - [Outliers](#outliers)
    - [Missing Data](#missing-data)
        - [Detection](#detection)
        - [Drop or Imputation](#drop-or-imputation)
    - [Categorical Data](#categorical-data)
      - [Get Dummies](#get-dummies)
    - [Vectorized String](#vectorized-string)
  - [Time-Series Data(pd. Series)](#time-series-datapd-series)
    - [Categorical Data](#categorical-data-1)
    - [](#)
  - [Load and Write Data](#load-and-write-data)

## Basic Data Structure and Creation

### Series

> - As we see in the output, the Series wraps both a sequence of values and a sequence of indices, which we can access with the values and index attributes.
> - The essential difference is the presence of the index: while the Numpy Array has an implicitly defined integer index used to access the values, the Pandas Series has an explicitly defined index associated with the values.
> - dictionary is a structure that maps arbitrary keys to a set of arbitrary values, and a Series is a structure which maps typed keys to a set of typed values. This typing is important: just as the type-specific compiled code behind a NumPy array makes it more efficient than a Python list for certain operations, the type information of a Pandas Series makes it much more efficient than Python dictionaries for certain operations.

created by

```python
pd. Series(values, [index=])
pd.series(dict, [index=])
```

attributes

- index
- both object and index have --name-- attribute

### DataFrame

> - DataFrame is an analog of a two-dimensional array with both flexible row indices and flexible column names. Just as you might think of a two-dimensional array as an ordered sequence of aligned one-dimensional columns, you can think of a DataFrame as a sequence of aligned Series objects. Here, by "aligned" we mean that they share the same index.

Creation

[pd.DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)

```python
# From series 
pd.DataFrame(series, columns = )
# From List of dictionaries 
pd.DataFrame(<list of dict>, (aligned in rows)
# from a Dictionary of series  (aliegned incolumns)
pd.DataFrame(<dict of series>, (aligned in rows)
## from Two-dimensioanl numpy array 
pd.DataFrame(<numpy>, columns = , index =)
```

Attributes

- df.index
- df.columns
- pd.dtypes - display the dtype of every column
  - float, datetime, category, object...
  - pd.Categorical()
    - pd.get_dummies(categorical data, prefix) - create dummy variables

### Index

> both the Series and DataFrame objects contain an explicit index that lets you reference and modify data. This Index object is an interesting structure in itself, and it can be thought of either as an immutable array or as an ordered set (technically a multi-set, as Index objects may contain repeated values). Those views have some interesting consequences in the operations available on Index objects

- index

#### Hirerachical Index

- [Multiindex](https://pandas.pydata.org/docs/user_guide/advanced.html)

## Data Manipulation

methods can be chained ( linked all together by .)

### Data Selection : Indexing and Slicing (and Add/Modify in place)

- df.col name - select one column
- df[col name/ col name list] - select a column
- df[index range] -select a number of rows
- df.filter(regrex = [regular expression]): search columns whose name matches
- df.--loc--([index range/index value, column list/column name] -select by label
  - df.at[row pos,col pos] 
- df.i--loc--[row positions, [column positions]]
  - df.iat[row position, column position]
- df[ --logic expression--] - logical indexing
  - df[ df/col.isin(vals]
  - df.drop_duplicates()
- df.head(n), df.tail(n)
- df.sample(frac = [frac]/n = [sample size]) :select a fraction of rows randomly
- df.nlargest(n, 'value'), df.nsmallest(n, 'value')

### Operation on Data

df.

- query(expr)
  - see how an expression is expressed if in Pandas
- stats
  - mean([axis])
  - var, std, skew, kurty
  - mad
- Mathematics
  - sub(df)
  - cumsum(), cummax(), cummin(), cumprod()
  - rank(method = [dense/min/first/max/average], pct = [Ture/False])
  - shift([n])
  - pct_change()
- String Operations
  - str.oper func()

summarize

- is_unique(), unique()
- .nunique() - counts unique values in each col
- .value_counts(): produce a histogram
- len(）
- describe()
- idx: labels, arg: positions
- argmin, argmax, idxmin, idxmax
- sum(), min(), max(), mean(), median(), var(), std()
- arguments
  - axis, skipna, level 
- count()
- quantile

#### Mathematical Operations

- +-/- - Operate on values

#### Modify

df.

- [reindex](https://pandas.pydata.org/pandas-docs/version/0.22.0/generated/pandas.DataFrame.reset_index.html)( index = index, columns = list)
- rename(index =, columns = func)
- shift(shift num)
- T 
  - transpose
- sort_index([axis], [b], [ascending])
- modify values
  - add, radd, sub, rsub, div, rdiv, floordiv, rfloordiv, mul, rmul, pow, rpow

#### Bining

pd

- cut(df, bins)
  - key would be intervals
- qcut

#### View/ Conversion to other types

df.

- copy
- index, columns,
  - returns Index
- values
  - returns Numpy nd-array

##### Random Samples

df.

- take(sample func-a random permutation)
- sample

### Functions

df.

- apply
- apply_map

use with lambda functions

#### Windows

df.

- expanding()
- rolling()

## Aggregation and Grouping

[Merge, Join and Concantenate](https://pandas.pydata.org/pandas-docs/stable/user_guide/merging.html)

pd.

- merge
- concat

[Grouping](https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html)

pd.

- groupby(key,[axis], [level=index name],[as index],[group_keys]).[columns].aggregator
  - keys
    - column name
    - dictionary or series (mapping)
      - map column (row) name to different values then group by values
    - function
      - eg.len
    - Categorial object
      - eg. ones returned by [pd.cut](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html)
  - aggregator
    - count, sum, mean, media, sts, var, min, max
    - prod
    - first, last - Non NA Values
    - aggregate(lambda or list of lambda functions) or agg(lambda)
      - aggregate([(func1,lambda1),(func2,lambda2)
        - give column names when aggregate using lambda
    - --apply --- most general form
      - function is called on each row group from the data frame, then the results are glued together with pandas.concat()
  - as index
    - not allow group keys to be hierarchical indices
  - group_keys
    - not allow group keys, use as original columns
- looping
  - for (k1, k2...), v in grouped
- groupby(key1)['data1']
  - syntactic sugar for df['data1'].groupby(df['key1'])

### Pivot Table

Special case of groupby

- [pd.pivot_table](https://pandas.pydata.org/docs/reference/api/pandas.pivot_table.html)(df, values=col name, index=cols name,  columns=[col to putin], [arrgfunc=np.mean])
  - can pass a dictionary to aggfunc
  - margins: compute totals along each grouping
- df.pivot_table([cols fo pivot],index=, [columns],[margins],[aggfun=],[fill_value=],[drop_na])_
  - margins=True will include partial total
  - default aggfunc is mean
- [df.pivot](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.pivot.html)(cols,vals)
- [pd.crosstab](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.crosstab.html)
  - special type of pivot table
- <pivot_table>.plot()
  - yiled a graph along axises directly

### Pandas Sql

```py
from pandasql import sqldf

def pysqldf(q):
  return sqldf(q, globals())

q = '''
SELECT - 
FROM df_uk_rain a LEFT JOIN df_right b
ON a.year = b.year
LIMIT 5
'''

pysqldf(q）
```

#### Combine DataSets

df[df.col.isin( a col in another df)],df[df.col.isin( a col in another df)],

- - append(rows, ignore_index = [T/F])



## Data Preprocessing

### Descriptive

df.

- head(), tail()
- info()
- describe()
- isnull.sum(), notnull().sum
- plot()
  - plot.hist()
  - plot.scatter()

#### Pandas Data Profiling

```py
import pandas_profiling
pandas_profiling.ProfileReport(df)
```

### Reshaping

- df.stack(): compress a level in the data frame's columns ( columns become a level index)

  - [unstack](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.unstack.html)([index level]):unstack a index level to column

- pd.melt(df, [indexes] ) : columns not in indexes are concated by different value combinations as rows

### Duplication

df.

- duplicated - returns boolean (duplicated rows)
  - _[np.where(df_uk_rain[['water_year', 'rain_octsep']].duplicated())]_
- drop_duplicates()

### Outliers

use boxplot and winsorizing

### Missing Data

##### Detection

df.

- [isna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isna.html)
- isnull
- notnull

can combine with any()

##### Drop or Imputation

df.

- [dropna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html)
- [fillna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html)(method)
  - method = 'ffill', method = 'bfill'
- fill with model

```py
# fill with model
clf = KNeighborsClassifier(3, weights='distance')
clf.fit(X_no_nan[['age', 'preMLScore', 'postMLScore']], X_no_nan['gender'])
x_imputed = clf.predict(X_with_nan[['age', 'preMLScore', 'postMLScore']])
X_with_imputed = X.copy()
X_with_imputed.loc[idx_with_nan,'gender'] = x_imputed.reshape(-1, 1)
X_with_imputed
```

### Categorical Data

#### Get Dummies

Converting categorical data to "dummy" or "indicator" matrix

df.

- get_dummies()
  - returns dummy variables
  - get_indexer
  - add_prefix

### Vectorized String

df.str

- contains
- findall(pattern, flag)
- extract
- cat
- count
- endswith, startswith
- findall, get, isalnum, isalpha, isdecimal, isdigit, islower, isnumeric, isupper
- join, len, lower, upper
- match
- pad
- cetner
- repear
- replace
- split
- strip, lstrip, rstrip

---

## Time-Series Data(pd. Series)

df.

- resample(arg).func()
  - aggregators : max, mean....
    - olhc
- rolling().func (apply)
  - rolling window function
- tz_localize()
- tz_convert()
- to_period()
  - convert to period data
- to_timestamp()

pd

- to_datetime()
- date_range()
- period_range(,[freq])
  - asfreq()

### Categorical Data

- df[cols].astype("category")
- df.cat
  - categories()
  - set_categories()
- df.sort_values(by)

### 



## Load and Write Data

df.

- to_csv(), 
- read__csv(filename ,[args]), read_table(file_name, [args])_
  - sep = "|", ","", "t"
  - names = names 
  - encoding
- to_hdf(), 
- to__excel(), read_excel_

pd.

- [read_csv](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)
  - nrows
  - chucksize
    - returns in chunckers
  - TextParser
- [to_csv](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html)
- ExcelFile
- [read_excel](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_excel.html)
- [to_excel](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_excel.html)
- read_html
- read_pickle(), to_pickle
  - to binary format
  - other formats
    - bcolz
    - Feather
- HDFSTore
  - returns HDF5 object with dict-like API
    - 2 storage schemas : 'fixed' 'table' - latter slightly slower
    - methods
  - - put
      - select
- to_hdf
- read_hdf
- read_sql(command, db)