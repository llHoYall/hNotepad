---
layout: post
title: Module - multiprocessing
category: python
tags: python
---

&nbsp;

# Module - multiprocessing

```python
from multiprocessing import Process, Lock, Value
import time

def run(name, l, c):
    print(name, 'process is created.')
    fixed = 0
    while 1:
        l.acquire()
        if c.value > 0:
            c.value -= 1
            l.release()
            fixed += 1
            time.sleep(0.1)
        else:
            l.release()
            print(name, 'fixed', fixed, 'defects')
            break
            
if __name__ == '__main__':
    lock = Lock()
    count = Value('i', 10)
    
    dev_list = []
    for name in ['Kim', 'Lee', 'Park']:
        dev = Process(target=run, args=(name, lock, count))
        dev_list.append(dev)
        dev.start()
        
    for dev in dev_list:
        dev.join()
    
    print('All processes are finished.')
```

