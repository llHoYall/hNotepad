---
layout: post
title: Package
category: python
tags: python
---

&nbsp;

# Package

비슷한 모듈 여러 개를 묶어 패키지로 만들 수 있다.

패키지를 import할 때, 패키지에 있는 모듈들이 자동으로 import되지 않는다. 직접 import를 해야만 사용할 수 있다.

```python
import package.module
```

패키지로 구성하려는 디렉토리마다 `__init__.py` 파일을 넣어 준다. 이 파일은 빈 파일이어도 상관이 없고, 보통 패키지 및 각 모듈에 대한 설명등이 적혀있다. `__all__` 속성에 리스트 형태로 모듈을 적어주면 패키지를 import할 때 리스트에 있는 모듈을 import하게 된다.

```python
# __init__.py
__all__ = ["module1", "module2"]
```

같은 패키지 안의 모듈끼리 import를 할 수도 있다.

```python
# 같은 디렉토리 혹은 하위 디렉토리에 있는 모듈
from module import *
# 상위 디렉토리에 있는 모듈
from upper_dir.other_dir.module import module
# 같은 디렉토리 혹은 부모 디렉토리에 있는 모듈
from . import module
# 부모 디렉토리에 있는 모듈
from .. import module
from ..dir import module
```



