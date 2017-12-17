---
layout: post
title: Module - threading
category: python
tags: python
---

&nbsp;

# Module - threading

thread란 하나의 프로세스 내에서 진행되는 하나의 실행 단위를 뜻한다.

프로세스는 윈도우에서 여러 응용 프로그램을 각각 실행시키는 것처럼 독립적으로 실행되어 독립된 메모리 공간을 사용하지만, 멀티스레드는 하나의 프로세스 내에서 여러 스레드가 프로세스 공간의 메모리를 공유해서 사용할 수 있다.

----

### Thread

스레드를 사용하려면 일반적으로 threading.Thread를 상속받은 클래스 객체를 생성해 사용하며, 생성자를 재정의 하는 경우 반드시 Thread.\_\_init\_\_()을 수행해야 한다.

#### Methods

- **start()** : 스레드를 시작한다.
- **run()** : 스레드의 동작을 정의한다.
- **join([*timeout*])** : 스레드가 종료되기를 기다린다.

----

### Lock

하나의 프로세스에서 2개 이상의 스레드가 동시에 수행되는 경우, 스레드 간에 프로세스 공간의 메모리를 공유한다. 하나의 변수에 대해 2개 이상의 스레드가 변경을 하고자 하면 어떤 스레드가 먼저 수행되느냐에 따라 결과가 달라질 수 있다. 이러한 상태를 race condition 이라고 한다.

race condition을 방지하기 위해 Lock이라는 동기화 객체를 사용한다.

Lock 객체는 locked와 unlocked 상태를 갖는다.

#### Methods

- **acquire()** : unlocked 상태를 locked 상태로 바꾼다.
- **release()** : locked 상태를 unlocked 상태로 바꾼다.

----

```python
# Thread Example

from threading import Thread, Lock
import time

count = 10
lock = Lock()

class developer(Thread):
    def __init__(self, name):
        Thread.__init__(self)
        self.name = name
        self.fixed = 0
        
    def run(self):
        global count
        while 1:
            lock.acquire()
            if count > 0:
                count -= 1
                lock.release()
                self.fixed += 1
                time.sleep(0.1)
            else:
                lock.release()
                break
                
dev_list = []
for name in ['Kim', 'Lee', 'Park']:
    dev = developer(name)
    dev_list.append(dev)
    dev.start()
    
for dev in dev_list:
    dev.join()
    print(dev.name, 'fixed', dev.fixed)
```

