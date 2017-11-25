---
layout: post
title: Module - pickle
category: python
tags: python
---

&nbsp;

# Module - pickle

pickle 모듈은 파이썬의 객체를 파일로 읽거나 쓸 수 있게 해준다.

이 때, 파일은 반드시 바이너리 모드를 사용해야한다.

데이터를 기록할 때는 `dump()` 함수를 사용하고, 불러올 때는  `load()` 함수를 사용한다.

```python
# 모듈 임포트
import pickle

# 저장할 객체
colors = ['red', 'green', 'blue']

# 파일 열기
with open('filename', 'wb') as f:
	# 데이터 기록
    pickle.dump(colors, f)
    
# 파일 열기
with open('filename', 'rb') as f:
    # 데이터 불러오기
    data = pickle.load(f)
```

클래스의 객체를 불러올 때는 반드시 해당 클래스가 정의되어 있어야 한다.

```python
import pickle

# 저장할 클래스 객체
class test:
    var = None
c = test()
c.var = 'TEST'

with open('filename', 'wb') as f:
    pickle.dump(c, f)
    
with open('filename', 'rb') as f:
    d = pickle.load(f)
```

