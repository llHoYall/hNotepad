---
layout: post
title: Module - os
category: python
tags: python
---

&nbsp;

# Module - os

### os.path

#### Attributes

- **name** : 파이썬이 실행되는 운영체제의 이름을 나타낸다. 'nt', 'posix', 'mac' 등의 결과가 반환된다.
- **environ** : 환경변수를 나타내는 딕셔너리 속성이다.

#### Methods

- **abspath(*path*)** : 현재 경로를 prefix로 붙여서 입력받은 경로를 절대 경로로 바꿔서 반환한다.
- **access(*path*, *mode*)** : 입력받은 경로에대해 mode에 해당하는 작업이 가능한지 여부를 반환한다.
  - mode
    - F_OK : 해당 경로의 존재 여부를 확인
    - R_OK : 해당 경로의 읽기 가능 여부를 확인
    - W_OK : 해당 경로의 쓰기 가능 여부를 확인
    - X_OK : 해당 경로의 실행 가능 여부를 확인
- **basename(*path*)** : 입력받은 경로의 base name을 반환한다. abspath() 함수와 반대 기능이다.
- **commonprefix(*path_list*)** : 입력받은 path_list로부터 공통적인 prefix를 추출하여 반환한다. 단순 문자열 연산이므로 잘못된 경로가 나올 수 있다.
- **chdir(*path*)** : 입력받은 경로로 현재 작업 디렉토리의 위치를 변경한다.
- **dirname(*path*)** : 입력받은 파일/디렉토리의 경로를 반환한다.
- **execl(*path*, *arg0*, *arg1*, ...)** : 현재 프로세스에서 새로운 프로그램을 실행하며 반환은 하지 않는다. 다음과 같이 다양한 형태가 있는데, 'l'이 붙은 것은 인자의 수가 정해진 것이고, 'v'가 붙은 것은 args라는 튜플을 인자로 받는다. 'e'가 붙은 것은 환경변수를 받고, 'p'가 붙은 것은 환경변수의 path를 이용한다.
  - execle(path, arg0, arg1, ..., env)
  - execlp(file, arg0, arg1, ...)
  - execlpe(file, arg0, arg1, ..., env)
  - execv(path, args)
  - execve(path, args, env)
  - execvp(file, args)
  - execvpe(file, args, env)
- **exists(*path*)** : 입력받은 경로가 존재하면 True, 존재하지 않으면 False를 반환한다. 파일이나 디렉토리가 존재하지만 읽기 권한이 없는 경우에도 False를 반환할 수 있다.
- **expanduser(*path*)** : 입력받은 경로 안의 '~'를 현재 사용자 디렉토리의 절대 경로로 대체한다. '~\<user\>'를 입력하면 원하는 사용자의 홈 디렉토리 경로로 대체된다.
- **expandvars(*path*)** : path안에 환경변수가 있다면 확장한다. 환경변수는 os.environ에 정의된 것을 참조한다.
- **fdopen(*fd*[, *mode*[, *bufsize*]])** : 파일 디스크립터를 이용해 파일 객체를 생성한다. `from os import fdopen`을 사용한다.
- **getatime(*path*)** : 입력받은 경로에 대한 최근 접근 시간을 반환한다. 반환되는 값은 epoch (1970.01.01) 이후 초단위이다. 파일이 없거나 권한이 없는 경우에는 os.error 예외가 발생한다.
- **getctime(*path*)** : 입력받은 경로에 대한 생성 시간을 반환한다. (유닉스 등에서는 최근 변경 시간이 반환될 수도 있다.) 반환되는 값은 epoch (1970.01.01) 이후 초단위이다. 파일이 없거나 권한이 없는 경우에는 os.error 예외가 발생한다.
- **getcwd()** : 현재 작업 디렉토리의 경로를 반환한다.
- **getenv(*varname*[, *value*])** : 환경변수의 값을 얻어온다. 해당 환경변수가 없을 경우 value 값을 반환하며, value도 생략되면 None이 반환된다.
- **getmtime(*path*)** : 입력받은 경로에 대한 최근 변경 시간을 반환한다. 반환되는 값은 epoch (1970.01.01) 이후 초단위이다. 파일이 없거나 권한이 없는 경우에는 os.error 예외가 발생한다.
- **getpid()** : 현재 프로세스 아이디를 반환한다.
- **getsize(*path*)** : 입력받은 경로에 대한 바이트 단위의 파일 크기를 반환한다. 파일이 없거나 권한이 없는 경우에는 os.error 예외가 발생한다.
- **isabs(*path*)** : 입력받은 경로가 절대 경로이면 True, 그렇지 않다면 False를 반환한다. 입력받은 문자열만 갖고 판단한다.
- **isfile(*path*)** : 입력받은 경로가 파일이면 True, 그렇지 않다면 False를 반환한다. 입력받은 경로가 존재하지 않아도 False를 반환한다.
- **isdir(*path*)** : 입력받은 경로가 디렉토리이면 True, 그렇지 않다면 False를 반환한다. 입력받은 경로가 존재하지 않아도 False를 반환한다.
- **join(*path1*[, *path2*[, ...]])** : 해당 os 형식에 맞게 입력받은 경로를 연결한다. 중간에 절대 경로가 나오면 이전에 join된 경로는 제거된다.
- **listdir(*path*)** : 입력받은 경로에 존재하는 파일과 디렉토리 목록을 반환한다.
- **makedirs(*path*[, *mode*])** : 입력받은 경로에 해당하는 디렉토리를 재귀적으로 생성한다.이미 디렉토리가 생성되어 있거나 권한이 없을 경우 예외가 발생한다.
- **mkdir(*path*[, *mode*])** : 입력받은 경로에 해당하는 디렉토리를 생성한다.
- **normcase(*path*)** : 해당 os 형식에 맞게 입력받은 경로의 문자열을 정규화한다.
- **normpath(*path*)** : 입력받은 경로를 정규화한다. '.' (현재 디렉토리), '..' (상위 디렉토리) 와 같은 구분자를 최대한 삭제한다.
- **pipe()** : 파이프를 생성한다.
- **popen(*command*[, *mode*[, *bufsize*]])** : 인자로 전달된 command를 수행하며 파이프를 연다. `from os import popen`을 사용한다.
- **putenv(*varname*, *value*)** : 환경변수 varname을 value로 설정한다. 자식 프로세스에게 영향을 미친다.
- **remove(*path*)** : 입력받은 파일을 삭제한다.
- **removedirs(*path*)** : 입력받은 디렉토리를 재귀적으로 삭제한다.
- **rename(*src*, *dst*)** : src를 dst로 이름을 변경한다.
- **renames(*src*, *dst*)** : src를 dst로 이름을 변경한다. rename()과 달리 이동에 필요한 디렉토리를 자동으로 생성한다.
- **rmdir(*path*)** : 입력받은 디렉토리를 삭제한다.
- **split(*path*)** : 입력받은 경로를 디렉토리 부분과 파일 부분으로 나눈다. 실제 파일의 존재 여부는 확인하지 않는다.
- **splitdrive(*path*)** : 입력받은 경로를 드라이브 부분과 나머지 부분으로 나눈다. 실제 파일의 존재 여부는 확인하지 않는다.
- **splitext(*path*)** : 입력받은 경로를 확장자 부분과 그 외의 부분으로 나눈다. 실제 파일의 존재 여부는 확인하지 않는다.
- **stat(*path*)** : 입력받은 경로에 해당하는 정보를 얻어온다.
- **startfile(*path*[, *operation*])** : path를 os에서 지정된 프로그램으로 실행한다. operation으로 명시적으로 수행할 프로그램을 지정할 수 있다. system()을 사용하면 파이썬 프로그램의 실행이 잠시 멈추고 system()이 끝나길 기다리게 되고, startfile()을 사용하면 멈추지 않고 계속 실행된다.
- **strerror(*code*)** : 에러 코드에 해당하는 에러 메시지를 보여준다.
- **system(*command*)** : command를 실행하며, 성공한 경우 0을 반환한다.
- **umask(*mask*)** : umask를 설정한다. 수행되면 이전 mask 값을 반환한다. 이후 오픈되는 파일이나 디렉토리는 (mode & ~umask)가 적용된다.
- **unlink(*path*)** : 입력받은 경로를 삭제한다.
- **utime(*path*, *times*)** : 입력받은 경로에 해당하는 파일에 대해 access time과 modified time을 times로  수정한다.
- **walk(*top*[, topdown=True[, onerror=None[, followlinks=False]]])** : top으로 지정된 디렉토리를 순회하며 경로, 디렉토리명을 순차적으로 반환한다.

