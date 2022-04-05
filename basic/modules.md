# Frequently Used Modules

#### Built-in Algorithms

* bisect
  * bisect\__left, bisect\_right_

#### functools

* reduce\(\) - for functional programming
* partial - for functional programming
* wraps - for decorator usage

#### Itertools

[Itertools](https://docs.python.org/2/library/itertools.html)

* count\(&lt;start&gt;\) - infinite
* cycle\(\[list-like\]\) - infinite
* repeat\(&lt;ele&gt;, \[repeat count\]\)
* takewhile\(&lt;lambda&gt;, infinite iter\)
* chain\(iter1, iter2...\)
* groupby\(\) - groupby repeated elements

#### math

* math.e, pi
* ceil\(\), floor\(\)
* pow\(\),log\(\), sqrt\(\)
* sin\(\),sinh\(\)
* degrees\(\), redians\(\)

#### statistics

#### random

* random.choice\(&lt;choices&gt;\)
* randint, randrange, random\(\), uniform\(a,b\)
* sample\(range,sample size\)
* shuffle\(&lt;list&gt;\)

#### copy

* deepcopy

#### re

[regular expressions](https://www.rexegg.com/regex-quickstart.html)

* regex = re.complile\(pattern, flags\)
  * returns reg exp object
* re.split
  * more powerful than regular split

regex.

* findall
  * returns list
* finditer
  * returns iterator
* .search\(&lt;par&gt;, &lt;string&gt;\)
  * returns a match object
* split
  * break string into piece at each occurrence of pattern
* sub, subn
  * replace \(first n\)

---

### Common Data Structures

#### heapq - heap \(priority queue\)

* heapify
* heappop, heappush, heappushpop
* merge
* nlargest
* nsmallest

#### **Collections**

high performance container types

* namedtuple
  * inherits from tuple
  * supports reference by attribute name
* deque
  * append\(\), appendleft\(\)
  * clear\(\), count\(\)
* ChainMap
  * supports to search with different priorities 
* Counter\(\[iterable or mapping\]\)
  * missing ones count as 0
  * elements\(\) - return m\*key iterables
  * most\_common\(\[n\]\) - most common n keys
  * substract\(iterable-or-mapping\)
* OrderedDict
  * remembers the order, give out when their key is firstly created
  * can be sorted
  * .popitem\(last=True\)
    * **FIFO **or LIFO
* UserDict, UserList, UserString
* Defaultdict
  * \[\] as setdefut methods automatically default

#### datetime

from** datetime **import datetime, date, time

basic types

* date
* time
* datetime
* timedelta
* tzinfo

dt = datetime\(2011, 10, 29, 20, 30, 21\)

dt.

* fromtimestamp\(\[t\]\)
* timestamp\(\) - convert to timestamp
* day
* minute
* date\(\)
* time\(\)
* strftime\(&lt;format string&gt;\)
* strptime \(\[str\],&lt;format string&gt;\)
  * parse time string to time
* replace\(minute-0, second=0\)
* timedelta\(\)
  * a new type for time difference
* format string
  * %Y, %y, m, dm h, i, s, w\(weekday\),
  * %U \(week number\) of the year \[00, 53\]; Monday is considered the first day of the week , the day before firtst Sunday of the year are "week 0"
  * %z - UTC \(time zone offset as +HHMM or -HHMM\)
  * %F Shortcut for %Y - n%m -% d
  * % D Shortcut for %m / %d / %y \(04/18/12\)

timezone, astimezone, tzinfo

* the tzinfo attribute default is None

utcnow\(\) = get utc and change timezone

```py
>>> from datetime import datetime, timedelta, timezone
>>> tz_utc_8 = timezone(timedelta(hours=8)) # 创建时区UTC+8:00
>>> now = datetime.now()
>>> now
datetime.datetime(2015, 5, 18, 17, 2, 10, 871012)
>>> dt = now.replace(tzinfo=tz_utc_8) # 强制设置为UTC+8:00
>>> dt
datetime.datetime(2015, 5, 18, 17, 2, 10, 871012, tzinfo=datetime.timezone(datetime.timedelta(0, 28800)))

>>> utc_dt = datetime.utcnow().replace(tzinfo=timezone.utc)
>>> print(utc_dt)
2015-05-18 09:05:12.377316+00:00
# astimezone()将转换时区为北京时间:
>>> bj_dt = utc_dt.astimezone(timezone(timedelta(hours=8)))
>>> print(bj_dt)
```

#### dateutil

dateutil.parser 

