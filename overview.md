# What is Python?

## Basic Things to Know

- Python is a advanced scripting language 
  - \( source code -&gt;intepreter\) : source code --&gt; compiler --&gt; byte code -&gt; intepreter
  - [python virtual machine](https://www.geeksforgeeks.org/internal-working-of-python/)
  - no need for def main\(\), but you can run by if \_\_\__name\_\_\_ = 'main":
- Python is a strongly-typed language with dynamic reference
  - data types can change at run time
- Almost everything in python is an **object\(id, name\),** bind with names
  - dir\(\)-display names in the current local scope
  - Python is object oriented
- Python is a glue language
- Python is functional programing language
- Python is multi-purpose language
  - web: WSGI API, Django framework, Flask, cache, unit test, 
  - GUI: wxPython, PyQt
  - OS: linux, mac, NetBSD
  - game: 3D model
  - Data sicence: integrating with C, C++ and FORTRAN 
  - prototyping + production
- Python has weaknesses
  - single thread
    - global interpreter lock\(GIL\) determines interpreter can only execute one line at the same time
    - Python C extensions can use native multithreading \(in C or C++\) can run code parrallel without being impacted by GIL 

## Some references

Python coders

- [Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum) (Father of Python)
- Alex Martelli
- Daniel Greenfeld
- Miguel Grinberg