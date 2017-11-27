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
static PyObject* test_function(PyObject* self, PyObject* args) {
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
PyMODINIT_FUNC PyInit_test(void) {
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

&nbsp;

### Exception Handling

파이썬 내부에서 발생한 예외는 파이썬 인터프리터가 자동으로 검출하고 사용자에게 알려주지만 확장 모듈 안에서 발생한 에러는 직접 처리해야 한다.

```C
void PyErr_SetString(PyObject* type, const char* message);

// Example
static PyObject* test_division(PyObject* self, PyObject* args) {
  int quotient = 0;
  int dividend, divisor = 0;
  
  if (!PyArg_ParseTuple(args, "ii", &dividend, divisor))
    return NULL;
  
  if (divisor) {
    quotient = dividend / divisor;    
  }
  else {
    PyErr_SetString(PyExc_ZeroDivisionError, "divisor must not be zero");
    return NULL;
  }
  
  return PyBuildValue("i", quotient);
}

static PyMethodDef TestMethods[] = {
    {"division", test_division, METH_VARARGS, "division function \n return quotient, quotient is dividend / divisor"},
    {NULL, NULL, 0, NULL}
};
```

&nbsp;

### Memory Management

C/C++ 에서는 메모리를 동적할당할 때 개발자가 관리를 해야하지만, 파이썬은 레퍼런스 카운트를 자동으로 한다. 하지만, C확장 모듈에서는 개발자가 직접 관리를 해야한다.

파이썬 C API 함수의 인터페이스에 따라 레퍼런스의 소유권한을 넘겨주기도 하고 빌려주기도 한다.

- PyLong_FromLong() : 소유권을 함께 넘겨준다.
- Py_BuildValue() : 소유권을 함께 넘겨준다.
- PyTuple_GetItem() : 레퍼런스만 넘겨준다.
- PyList_GetItem() : 레퍼런스만 넘겨준다.
- PyDict_GetItem() : 레퍼런스만 넘겨준다.
- PyDict_GetItemString() : 레퍼런스만 넘겨준다.

C 함수가 파이썬에서 사용될 때, 함수 매개변수를 통해 빌려온 레퍼런스다 전달된다. 함수로 전달된 인자는 모두 빌려온 레퍼런스이므로 레퍼런스 카운트 감소를 할 필요가 없다. 호출한 곳에서는 함수가 정상적으로 수행될 때까지 빌려온 레퍼런스의 라이프타임을 보장해야한다. 따라서 레퍼런스 카운트 증가를 해야한다.

```C
// Example
tuple = PyTuple_GetItem(list, 1);	// 빌려온 레퍼런스
Py_INCREF(list);
long l = 0;
PyObject* item = PyLong_FromLong((long)l);	// 생성된 레퍼런스의 소유권한도 함께 전달된다.
Py_DECREF(item);
Py_DECREF(list);
```

```C
// Example
list = PyList_GetItem(list, 1);
long l = 0;
PyObject* item = PyLong_FromLong((long)l);
PyList_SetItem(list, l, item);	// 함수 호출이 실패하더라도 소유권한을 뺏어간다.
```

```C
// Example
void bug(PyObject* list) {
  PyObject* item = PyList_GetItem(list, 0);		// 레퍼런스를 받는다.
  Py_INCREF(item);	// 레퍼런스 카운트를 증가시켜 아이템에 대한 재배치 작업을 하지 않도록 한다.
  PyList_SetItem(list, 1, PyLong_FromLong(0L));	// 리스트의 아이템에 대한 모든 레퍼런스를 메모리 상에서 재배치하는 작업이 수행될 수도 있다.
  PyObject_Print(item, stdout, 0);
  Py_DECREF(item);
}
```

`Py_XINCREF()`와 `Py_XDECREF()`는 내부에서 NULL인지 파이썬의 None인지 검사하고 NULL일 경우 레퍼런스 카운트에 대한 작업을 무시한다.

```C
PyObject* item = NULL;
Py_XDECREF(item);
```

&nbsp;

### Reference

##### PyArg_ParseTuple

파이썬에서 C로 전달되는 인자를 C함수에 맞게 변경하는 함수이다.

```C
int PyArg_ParseTuple(PyObject* arg, char* format, ...);
```

| 파이썬 객체         | 기호   | C 자료형       |
| -------------- | ---- | ----------- |
| bytes object   | y    | const char* |
| int            | i    | int         |
| int            | l    | long        |
| float          | f    | float       |
| unicode object | s    | const char* |
| unicode object | u    | Py_UNICODE  |
| object         | O, S | PyObject    |

`s#` 기호를 사용한다면 문자열과 문자열 길이를 반환해준다.

```C
// Example
if (!PyArg_ParseTuple(args, "s#", &str, &len))
  return NULL;

// func(1, 2, 'test')로 호출하면 k = 1, l = 2, s ='test'가 저장된다.
ret = PyArg_ParseTuple(args, "lls", &k, &l, &s);

// func((1, 2), 'test')로 호출하면 튜플 안의 값을 읽어 k = 1, l = 2, s = 'test'로 저장된다.
ret = PyArg_ParseTuple(args, "(ll)s", &k, &l, &s);
```

##### Py\<*datatype*>_Check

파이썬이 전달하는 PyObject의 값이 어떤 타입인지 알고 있다면 `PyArg_ParseTuple` 함수를 사용할 수 있지만, 모를 경우에는 타입 검사를 하여 사용해야 한다.

```C
int PyInt_Check(PyObject* o);
int PyLong_Check(PyObject* o);
int PyFloat_Check(PyObject* o);
int PyComplex_Check(PyObject* o);
int PyString_Check(PyObject* o);
int PyBuffer_Check(PyObject* o);
int PyTuple_Check(PyObject* o);
int PyList_Check(PyObject* o);
int PyDict_Check(PyObject* o);

// Example
if (PyLong_Check(obj))
  ret = PyArg_ParseTuple(args, "l", &k);
else if (PyString_Check(obj))
  ret = PyArg_ParseTuple(args, "s", &s);
```

##### Py_BuildValue

C의 자료형을 파이썬의 자료형으로 변환하는 함수이다. 단, 매개변수가 포인터인 데이터는 사용할 수 없다. 매개변수가 비어 있으면 None 객체를 만든다.

```C
// Example
Py_BuildValue("");
Py_BuildValue("i", 123);
Py_BuildValue("iii", 1, 2, 3);
Py_BuildValue("s", "hello");
Py_BuildValue("s#", "hello", 5);
Py_BuildValue("()");	// ()
Py_BuildValue("(ii)", 1, 2);
Py_BuildValue("[ii]", 1, 2);
Py_BuildValue("{s:i, s:i}", "A", 1, "B", 2);
Py_BuildValue("((ii)(ii))(ii)", 1, 2, 3, 4, 5, 6);	// (((1, 2), (3, 4)), (5, 6))
```

##### PyErr_SetFromErrno

예외 발생 시 문자열 대신 C의 전역 변수인 errno 값을 반환해준다.

##### PyErr_SetObject

개발자가 전달하고 싶은 데이터를 반환해준다.

```C
if (val > 2)
  PyErr_SetObject(PyExc_IndexError, Py_BuildValue("l", val));
```

