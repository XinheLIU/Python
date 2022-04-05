### File

#### contextlib

contextlib

to work with the context manager \(context lib\)

@contextmanager takes a generator, use **yield** to give output var to **with**

```py
from contextlib import contextmanager

class Query(object):

    def __init__(self, name):
        self.name = name

    def query(self):
        print('Query info about %s...' % self.name)

@contextmanager
def create_query(name):
    print('Begin')
    q = Query(name)
    yield q
    print('End')


@contextmanager
def tag(name):
    print("<%s>" % name)
    yield
    print("</%s>" % name)

with tag("h1"):
    print("hello")
    print("world")

'''
<h1>
hello
world
</h1>
'''
```

@closing

convert objects to **context object**

```py
@contextmanager
def closing(thing):
    try:
        yield thing
    finally:
        thing.close()

from contextlib import closing
from urllib.request import urlopen

with closing(urlopen('https://www.python.org')) as page:
    for line in page:
        print(line)
```

#### IO

* stringIO

## Binary Data

#### base64

use 64-bits for binary data

* b64encode
* urlsafe\_b64encode

#### struct

the Bytes are represented by b'str' in python

```py
>>> n = 10240099
>>> b1 = (n & 0xff000000) >> 24
>>> b2 = (n & 0xff0000) >> 16
>>> b3 = (n & 0xff00) >> 8
>>> b4 = n & 0xff
>>> bs = bytes([b1, b2, b3, b4])
>>> bs
b'\x00\x9c@c'
```

struct supports the transformation of bytes and other binary data

struct

* pack\(&lt;command&gt;, &lt;data&gt;\)
  * transform to binary

#### chardet

[chardet](https://chardet.readthedocs.io/en/latest/index.html)

detect binary data encoding methods

```py
>>> data = '最新の主要ニュース'.encode('euc-jp')
>>> chardet.detect(data)
{'encoding': 'EUC-JP', 'confidence': 0.99, 'language': 'Japanese'}
```

### Hashing

#### hashlib

* md5 
* sha1
* sha256, sha512

instantiates an object

md5.

* update
* hexdigest

# Text

#### TextParser

[TextParser](#)

### csv

[csv](#)

* reader
* Dialect
  * define own class
    * delimiters, lineterminator, quotecchar, quoting, double quote

#### Json

[Json](#)

Json Inputs/Outputs

import JSON

* json.dumps\(\) - serialize python data type to string
* json.loads\(\) - de-serialize string to python data type

### XML and HTML

### xml

Two methods: SAX and DOM

* DOM read all XML into memory as a tree
* SAX use stream, must handle events

parser

* expat

```py
from xml.parsers.expat import ParserCreate

class DefaultSaxHandler(object):
    def start_element(self, name, attrs):
        print('sax:start_element: %s, attrs: %s' % (name, str(attrs)))

    def end_element(self, name):
        print('sax:end_element: %s' % name)

    def char_data(self, text):
        print('sax:char_data: %s' % text)

xml = r'''<?xml version="1.0"?>
<ol>
    <li><a href="/python">Python</a></li>
    <li><a href="/ruby">Ruby</a></li>
</ol>
'''

handler = DefaultSaxHandler()
parser = ParserCreate()
parser.StartElementHandler = handler.start_element
parser.EndElementHandler = handler.end_element
parser.CharacterDataHandler = handler.char_data
parser.Parse(xml)
```

#### lxml

* objectify
  * parse

parsed.

* get\_root
  * returns indicator object

#### HTMLParser

* feed supports multiple calls, can parse by part
  * special char:  , &\#1234 - could all be parsed

```py
from html.parser import HTMLParser
from html.entities import name2codepoint

class MyHTMLParser(HTMLParser):

    def handle_starttag(self, tag, attrs):
        print('<%s>' % tag)

    def handle_endtag(self, tag):
        print('</%s>' % tag)

    def handle_startendtag(self, tag, attrs):
        print('<%s/>' % tag)

    def handle_data(self, data):
        print(data)

    def handle_comment(self, data):
        print('<!--', data, '-->')

    def handle_entityref(self, name):
        print('&%s;' % name)

    def handle_charref(self, name):
        print('&#%s;' % name)

parser = MyHTMLParser()
parser.feed('''<html>
<head></head>
<body>
<!-- test html parser -->
    <p>Some <a href=\"#\">html</a> HTML&nbsp;tutorial...<br>END</p>
</body></html>''')
```

### Image

#### Pillow

[Pillow](https://pillow.readthedocs.io/en/stable/)

**pyTables**

**h5Py**

