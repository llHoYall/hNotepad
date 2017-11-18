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
# 모듈에 있는 모든 내용을 import 한다.
import module_name
# '모듈.어트리뷰트' 대신 '어트리뷰트'를 바로 사용할 수 있다.
from module_name import attribute
# 모듈에 있는 내용 중 '_'로 시작하는 내용은 제외하고 import 한다.
from module_name import *
# 모듈을 import할 때 다른 이름으로 import 한다.
from module_name as alias
```

모듈을 import할 때, 다음의 순서로 모듈을 찾는다.

1. 현재 작업 디렉토리
2. PYTHONPATH 환경변수에 등록된 위치
3. 표준 라이브러리 디렉토리

표준 라이브러리 디렉토리의 위치는 `sys.path`에 리스트 형식으로 관리되고 있다. 런타임에도 `sys.path.append(module)`, `sys.path.remove(module)`을 통하여 직접 관리할 수 있다. 

모듈을 import하면 인터프리터가 바이트코드를 만들어 import 한다. *.pyc 파일이 바이트코드로 된 파일이다. 바이트코드는 인터프리팅 되지 않고 바로 메모리에 로딩되므로 import가 빨라진다. 모듈의 내용이 변경되지 않는 이상 바이트코드는 새로 만들어지지 않는다.

모듈이 한 번 import되면 메모리에 모듈 코드가 로딩되고 프로그램이나 인터프리터가 끝나기 전까지 변경되지 않는다. 모듈이 수정될 경우 프로그램이나 인터프리터를 종료하고 재시작 하여 다시 import 해야한다.

```python
# 재시작 없이 모듈을 로딩하는 방법.
import imp
import module_name
imp.reload(module_name)
```

모듈을 서로 다른 이름으로 여러 번 로딩 할 경우, 레퍼런스만 여러 개 생기고 메모리의 모듈 내용은 공유된다.

`__name__` 속성은 모듈이 직접 실행될 경우 `__main__`이라는 값으로 설정되고, import될 경우 모듈의 이름으로 설정된다.

```python
if __name__ == '__main__':
    print("직접 실행")
else:
    print("imported")
```

##### Create

원하는 모듈의 이름으로 module_name.py 라는 파일을 만들면, 곧 모듈이 된다.