---
layout: post
title: distutils
category: python
tags: python
---

&nbsp;

# distutils

distutils는 플랫폼에 종속되지 않고 프로그램을 배포해줄 수 있게 도와주는 툴이다.

단, 스크립트를 사용하기 때문에 플랫폼에 따라 스크립트를 따로 관리해줘야 한다.

### 기본 사용법

##### 배포용 스크립트

다음의 예제처럼 배포를 하고자 하는 내용을 스크립트로 작성하자. 관례적으로 setup.py라는 이름을 사용한다. 필요한 코드들은 모두 setup.py가 있는 곳에 있어야 한다.

```python
# setup.py

from distutils.core import setup

setup(
    name='test',
    version='1.0',
    py_modules=['test'],
)
```

##### 배포 절차

다음 명령을 실행하면 배포할 내용을 묶어 dist 디렉토리 안에 압축 파일로 만들어 준다. 이 압축 파일을 배포하면 된다.

소스코드 형태로 배포하려면 sdist (source distribution), 바이너리 형태로 배포하려면 bdist (binary distribution)를 사용한다. bdist를 사용하면 소스코드와 바이트코드가 함께 포함된다.

> $ python setup.py sdist
> $ python setup.py bdist

윈도우즈용으로 인스톨러를 만들어 배포하려면 bdist_wininst, 리눅스용으로 인스톨러를 만들어 배포하려면 bdist_rpm을 사용한다.

> $ python setup.py bdist_wininst
> $ python setup.py bdist_rpm

##### 설치

배포한 압축 파일을 받은 사용자는 압축을 풀고 다음 명령을 실행하여 설치를 한다.

> $ python setup.py install

### setup.py 파일 작성법

##### Meta-Data

- **name** : 패키지 이름. 짧은 문자열.
- **version** : 릴리즈 버전. 짧은 문자열.
- **author** : 패키지 제작자. 짧은 문자열.
- **author_email** : 패키지 제작자의 email 주소. 이메일 주소.
- **maintainer** : 패키지 관리자 이름. 짧은 문자열.
- **maintainer_email** : 패키지 관리자의 email 주소. 이메일 주소.
- **url** : 패키지의 홈페이지.
- **description** : 패키지에 대한 짧은 설명. 짧은 문자열.
- **long_description** : 패키지에 대한 자세한 설명. 긴 문자열.
- **download_url** : 다운로드 url. URL.
- **classifiers** : 패키지 구분자 리스트. 리스트.
- **platforms** : 플랫폼 리스트. 리스트.

짧은 문자열은 200자 이하의 한 줄 짜리 텍스트, 긴 문자열은 한 줄 이상의 텍스트를 말한다.

##### Package 포함

```python
# root
#	ㄴ setup.py
#	ㄴ package
#		ㄴ __init__.py
#		ㄴ file1.py
#		ㄴ sub_package1
#			ㄴ __init__.py
#			ㄴ file2.py
#			ㄴ file3.py
#		ㄴ sub_package2
#			ㄴ __init__.py
#			ㄴ file4.py
#			ㄴ file5.py

from distutils.core import setup, Extention

# sub_package들을 제외한 package 자체만 포함한다.
setup(
    name='package',
    version='1.0',
    classifiers=['package::file1'],
    packages=['package'],
)

# 전체 package를 포함한다.
setup(
    name='package',
    version='1.0',
    classifiers=['package', 'package::file1', 'package::sub_package1::file2', 'package::sub_package1::file3', 'package::sub_package2::file4', 'package::sub_package2::file5'],
    packages=['package', 'package.sub_package1', 'package.sub_package2'],
)

# sub_package1만 포함한다.
setup(
    name='package',
    version='1.0',
    classifiers=['package::sub_package1::file2', 'package::sub_package1::file3'],
    packages=['package.sub_package1'],
    package_dir={'': 'package'}
)
```

### 확장 모듈 배포

C를 이용한 확장 모듈등도 distutils를 이용해 배포할 수 있다.

```python
from distutils.core import setup, Extension

setup(
    name='module',
    version='1.0',
    ext_package='pkg',
    ext_modules=[
        Extension('module', ['module.c'], 
                  include_dirs=['../inc', './sub_module/inc'], 
                  libraries=['lib1'], 
                  library_dirs=['C:\\Python36\\Lib'],
                  runtime_library_dirs=['path']
                 ),        
        Extension('module.sub_module', ['sub_module.c'], 
                  define_macros=[('DEFINE', 'VALUE')]
                 )
    ],
    data_files=[('xml', ['file.xml', 'image.jpg']), ('config', 'config.cfg')]
)
```

### Setup Configuration

setup.cfg 파일을 사용하여 하나의 setup.py 파일을 이용하여 다양한 빌드를 할 수 있다.

파일의 구조는 다음과 같다.

```python
[<command>]
<option>=<value>
```

사용 가능한 명령의 목록을 보려면 다음 명령을 실행한다.

> $ python setup.py --help-commands
>
> // Options for 'sdist' command
> $ python setup.py --help sdist

```python
# sdist일 때, sdist_pkg 디렉토리에 배포 패키지를 생성한다.
[sdist]
dist_dir=sdist_pkg

# bdist일 때, bdist_pkg 디렉토리에 배포 패키지를 생성한다.
[bdist]
dist_dir=bdist_pkg
```

