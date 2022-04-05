### Web API

#### urlib

urllib.request

Request\(&lt;link&gt;\)

request object

* add\_header
  * add HTTP header - to be like a browser
  * pass in data \(bytes format\) - POST a request
* getheaders

request.

* urlopen - context object

handler

urlib.request.ProxyHandler

ProxyBasicAuthHandler

#### requests

* get\(&lt;url&gt;, params\)
  * returns a webpage object
* post\(&lt;url&gt;, data\)
* put
* delete

web object

* status\_code
* text
* url
* encoding
  * utf-8

```py
>>> r = requests.get('https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20weather.forecast%20where%20woeid%20%3D%202151330&format=json')
>>> r.json()
{'query': {'count': 1, 'created': '2017-11-17T07:14:12Z', ...
```

#### Beautiful Soup

HDF5

### 

---

# Database

## Connect with SQL

#### API

Follow [Python DB API](https://www.python.org/dev/peps/pep-0249/) Standards

* mysql-connector
* MySQLdb
* mysqlclient
* PyMySQL

#### ORM Framework

*  SQLAlchemy
  * session
  * datatypes
* Django
  * models
* peewee

Mapping

* Column &lt;--&gt; Table
* Column instance -&gt; row
* Attributes -&gt; SQL fields

sqlite3

* connect\(&lt;sqlite file&gt;\) - returns connection
* connections
* * execute - returns cursor
  * executemany
  * commit\(\)
* cursor
  * fetchall
    * display the data
  * description

sqlalchemy

sqla

* create\_engine\(\)



