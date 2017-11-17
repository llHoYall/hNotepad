---
layout: post
title: Module
category: python
tags: python
---

&nbsp;

# Module

모듈을 만듦으로 코드를 재사용할 수 있다.

모듈은 자기 자신의 이름으로 namespace를 갖는다.

##### Import

내장 모듈이나 다른 사람이 만든 모듈, 자신이 만든 모듈을 가져와서 사용할 수 있다.

```python
import module_name
from module_name import symbol
from module_name import *
```

모듈을 import할 때, 다음의 순서로 모듈을 찾는다.

1. 현재 작업 디렉토리
2. PYTHONPATH 환경변수에 등록된 위치
3. 표준 라이브러리 디렉토리

표준 라이브러리 디렉토리의 위치는 `sys.path`에 리스트 형식으로 관리되고 있다. 런타임에도 `sys.path.append(module)`, `sys.path.remove(module)`을 통하여 직접 관리할 수 있다. 

##### Create

원하는 모듈의 이름으로 module_name.py 라는 파일을 만들면, 곧 모듈이 된다.