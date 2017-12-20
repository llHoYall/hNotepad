---
layout: post
title: Module - socket
category: python
tags: python
---

&nbsp;

# Module - socket

Low-level 네트워킹 인터페이스 모듈이다.

```python
# server.py

import socket

HOST = ''
PORT = 50007
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((HOST, PORT))
s.listen(1)
conn, addr = s.accept()
print('Connected by', addr)
while True:
    data = conn.recv(1024)
    if not data:
        break
    conn.send(data)
conn.close()
```

```python
# client.py

import socket

HOST = '127.0.0.1'
PORT = 50007
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((HOST, PORT))
s.send(b'Hello, Python')
data = s.recv(1024)
s.close()
print('Received', repr(data))
```

