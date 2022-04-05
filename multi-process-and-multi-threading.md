## Basic Concepts

* [Process and Thread](https://www.geeksforgeeks.org/difference-between-process-and-thread/)
* [fork](http://man7.org/linux/man-pages/man2/fork.2.html) command in linux
* Computation Intensive and I/O intensive
  * [I/O bound](https://en.wikipedia.org/wiki/I/O_bound)
* [Asynchronous I/O](https://en.wikipedia.org/wiki/Asynchronous_I/O)

## Multiprocessing

* use fork \(Unix-like system only\)

  * ```py
    import os

    print('Process (%s) start...' % os.getpid())
    # Only works on Unix/Linux/Mac:
    pid = os.fork()
    if pid == 0:
        print('I am child process (%s) and my parent is %s.' % (os.getpid(), os.getppid()))
    else:
        print('I (%s) just created a child process (%s).' % (os.getpid(), pid))
    ```

* use [multiprocessing](https://docs.python.org/2/library/multiprocessing.html) module

  * ```py
    from multiprocessing import Process
    import os

    # subprocess code
    def run_proc(name):
        print('Run child process %s (%s)...' % (name, os.getpid()))

    if __name__=='__main__':
        print('Parent process %s.' % os.getpid())
        p = Process(target=run_proc, args=('test',))
        print('Child process will start.')
        p.start()
        p.join()
        print('Child process end.')
    ```

* use pool \(for many sub-processes\)

  * ```py
    from multiprocessing import Pool
    import os, time, random

    def long_time_task(name):
        print('Run task %s (%s)...' % (name, os.getpid()))
        start = time.time()
        time.sleep(random.random() * 3)
        end = time.time()
        print('Task %s runs %0.2f seconds.' % (name, (end - start)))

    if __name__=='__main__':
        print('Parent process %s.' % os.getpid())
        p = Pool(4)
        for i in range(5):
            p.apply_async(long_time_task, args=(i,))
        print('Waiting for all subprocesses done...')
        p.close()
        p.join()
        print('All subprocesses done.')
    ```

* subprocess

  * ```py
    import subprocess

    print('$ nslookup')
    p = subprocess.Popen(['nslookup'], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    output, err = p.communicate(b'set q=mx\npython.org\nexit\n')
    print(output.decode('utf-8'))
    print('Exit code:', p.returncode)
    ```

* process communication

  * Queue and Pipes methods

    * ```py
      from multiprocessing import Process, Queue
      import os, time, random

      # writing data
      def write(q):
          print('Process to write: %s' % os.getpid())
          for value in ['A', 'B', 'C']:
              print('Put %s to queue...' % value)
              q.put(value)
              time.sleep(random.random())

      # reading data
      def read(q):
          print('Process to read: %s' % os.getpid())
          while True:
              value = q.get(True)
              print('Get %s from queue.' % value)

      if __name__=='__main__':
          # queue created by paren
          q = Queue()
          pw = Process(target=write, args=(q,))
          pr = Process(target=read, args=(q,))
          # pw is writing sub-process, pr is reading
          pw.start()
          pr.start()
          # wait for pw to end
          pw.join()
          # pr is a dead loop, must terminate
          pr.terminate()
      ```

### Distributed Multi-processing

* use Manager object
* communication using Queue. QueueManger will expose Queue to network and visited by another machine \(with authkey\)
* Master/Worker.

---

## Multithread

### Modules

* [\_thread ](https://docs.python.org/3/library/_thread.html)low level threading API
* [threading](https://docs.python.org/3/library/_thread.html) high level interface

### Running thread and use Lock

```py
import time, threading

# 假定这是你的银行存款:
balance = 0

def change_it(n):
    # 先存后取，结果应该为0:
    global balance
    balance = balance + n
    balance = balance - n

def run_thread(n):
    for i in range(100000):
        # 先要获取锁:
        lock.acquire()
        try:
            # 放心地改吧:
            change_it(n)
        finally:
            # 改完了一定要释放锁:
            lock.release()

t1 = threading.Thread(target=run_thread, args=(5,))
t2 = threading.Thread(target=run_thread, args=(8,))
t1.start()
t2.start()
t1.join()
t2.join()
print(balance)

# lock
balance = 0
lock = threading.Lock()
```

### Global Interpreter lock

[Global Interpreter lock](https://wiki.python.org/moin/GlobalInterpreterLock)

### ThreadLocal

* a special global variable to let each thread independently read/write attributes \(like a global dictionary\)
* no need to pass local variable to each local function specifically any more

```py
import threading

# 创建全局ThreadLocal对象:
local_school = threading.local()

def process_student():
    # get current thread student:
    std = local_school.student
    print('Hello, %s (in %s)' % (std, threading.current_thread().name))

def process_thread(name):
    # bond with ThreadLocal student:
    local_school.student = name
    process_student()

t1 = threading.Thread(target= process_thread, args=('Alice',), name='Thread-A')
t2 = threading.Thread(target= process_thread, args=('Bob',), name='Thread-B')
t1.start()
t2.start()
t1.join()
t2.join()
'''
Hello, Alice (in Thread-A)
Hello, Bob (in Thread-B)
'''
```

---

## Asynchronous I/O

### Coroutine

[Coroutine ](https://en.wikipedia.org/wiki/Coroutine)and subroutines are popular in parallel computing \(Lua\) \(Multiprocessing + coroutine\). In python this is done by generators

```py
def consumer():
    r = ''
    while True:
        n = yield r
        if not n:
            return
        print('[CONSUMER] Consuming %s...' % n)
        r = '200 OK'

def produce(c):
    c.send(None)
    n = 0
    while n < 5:
        n = n + 1
        print('[PRODUCER] Producing %s...' % n)
        r = c.send(n)
        print('[PRODUCER] Consumer return: %s' % r)
    c.close()

c = consumer()
produce(c)
```

### Asyncio

[asyncio](https://docs.python.org/3/library/asyncio.html) is the library for concurrent code. The asynchronous operation is done in coroutine by yield from. Multiple coroutines can be packed into one task. It uses a[ event loop](https://en.wikipedia.org/wiki/Event_loop) pattern.

* async = @asyncio.coroutine decorator 
* await = yield from 

```py
import threading
import asyncio

# @asyncio.coroutine
async def hello():
    print('Hello world! (%s)' % threading.currentThread())
    # yield from asyncio.sleep(1)
    await asyncio.sleep(1)
    print('Hello again! (%s)' % threading.currentThread())

loop = asyncio.get_event_loop()
tasks = [hello(), hello()]
loop.run_until_complete(asyncio.wait(tasks))
loop.close()
```

#### Aiohttp

[aiohttp](https://docs.aiohttp.org/en/stable/) implements HTTP framework based on asyncio \(has TCP/UDP/SSL protocols\) 





