---
layout: post
title: C/C++
category: python
tags: python
---

&nbsp;

# C/C++

C/C++와 연동을 할 수 있다.

C/C++ 파일을 생성한다. 보통 '모듈이름+module.c'와 같은 형식을 사용한다.

다음으로, `python.h` 헤더를 포함한다. 이 헤더안에는 `stdio.h, string.h, error.h, limits.h, stdlib.h` 가 포함되어 있다.

```C
// testmodule.c
#include <python.h>

// 파이썬의 객체를 C의 데이터 타입으로 표현할 수 있는 구조체.
static PyObject *

test_function(PyObject* self, PyObject* args) {
	const char* str = NULL;
	int len = 0;
	
	// 파이썬에서 전달된 인자를 C의 자료형으로 변환해준다.
	if (!PyArg_ParseTuple(args, "s", &str))
		return NULL;
	
    // TODO: C/C++로 처리할 내용
    len = strlen(str);
 
 	// C의 자료형을 PyObject로 변환한다.
    return Py_BuildValue("i", len);
}
```

이 모듈을 파이썬에서 불러와야 한다. 모듈을 import하면 파이썬 내부에서 다음과 같은 작업을 한다.

1. 모듈을 찾는다.
2. 모듈을 초기화한다.
3. Local namespace에 이름을 정의한다.

C/C++로 만든 모듈을 파있썬에서 import하려면 C/C++에서 2, 3단계를 직접 처리해줘야 한다.

```C
static PyMethodDef TestMethods[] = {
    {"strlen", test_function, METH_VARARGS, "count a string length."},
    {NULL, NULL, 0, NULL}
};

static struct PyModuleDef testmodule = {
    PyModuleDef_HEAD_INIT,
    "test",		// Module Name
    "It is a test module.",		// Description. __doc__에 저장된다.
    -1,
    TestMethods
};

// 모듈을 초기화한다.
PyMODINIT_FUNC
PyInit_test(void) {
	return PyModule_Create(&testmodule);
}
```

초기화 함수의 이름은 반드시 PyInit_\<*module_name*> 이어야 한다.

PyMethodDef 구조체는 파이썬에서 사용할 함수 이름, 실행될 함수 포인터, 파이썬에서 호출 시 인자를 어떻게 받을지 결정하는 상수, 함수 설명으로 되어 있다. 

- METH_VARARGS : 튜플 형태로 받는다.
- METH_KEYWORDS : 딕셔너리 형태로 받는다.

이제 작성된 C 파일을 빌드해야한다. 간편하게 distutils를 사용한다.

```python
# setup.py
# usage: $ python setup.py install
from distutils.core import setup, Extension
test_mod = Extension('test', sources = ['testmodule.c'])
setup(name = "test",
     version = "1.0",
     description = "A sample extension module",
     ext_modules = [test_mod],
)
```

이제 빌드된 모듈을 파이썬에서 import하여 사용할 수 있다.

```python
# link_with_c_c++.py
import test

strcnt = test.strlen("test");
print(strcnt)
```

