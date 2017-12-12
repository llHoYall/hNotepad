---
layout: post
title: Module - glob
category: python
tags: python
---

&nbsp;

# Module - glob

디렉토리 탐색 기능을 하는 모듈이다.

#### Methods

- **glob(*path*)** : 입력받은 경로에 대응되는 모든 파일 및 디렉토리 목록을 리스트로 반환한다. '*', '?' 같은 문자도 사용 가능하며, '[ ]'를 이용하여 문자 그룹도 사용 가능하다.
- **iglob(*path*)** : glob()과 동일하나 이터레이터를 반환한다.

```python
import glob

print(glob.glob('test?.*'))
print(glob.glob('test[0-9].*'))
print(glob.glob(abspath('.') + '\\*.exe'))

for i in glob.iglob('*'):
    print(i)
```

