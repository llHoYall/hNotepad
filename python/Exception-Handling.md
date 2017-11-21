---
layout: post
title: Exception Handling
category: python
tags: python
---

&nbsp;

# Exception Handling

예외 처리는 다음과 같은 문법을 사용한다.

```python
try:
    # 예외 발생 가능성이 있는 처리
except <exception>:
    # 원하는 예외 처리
except (exception1, exception2):
    # 에러의 종류는 다르지만 같은 예외 처리
except exception as argument:
    # 예외에 대한 정보와 함께 예외 처리
except:
    # 나머지 모든 예외 처리
else:
    # 예외가 발생하지 않은 경우 수행
finally:
    # 무조건 수행
```

사용 예는 다음과 같다.

```python
def divide(a, b):
    return a / b

try:
    c = divide(5, 2)
except ZeroDivisionError:
    print('두 번째 인자는 0이 아니어야 한다.')
except (OverflowError, FloatingPointError):
    print('수치 연산 에러')
except TypeError as e:
    print('모든 인자는 숫자여야 한다. ', e.args[0])
except:
    print('나머지 에러')
else:
    print('Result: {0}'.format(c))
finally:
    print('Finished')
```

예외 클래스 계층 구조에서 부모 클래스를 `except` 구문으로 처리하면 부모 클래스를 상속받은 하위 모든 클래스도 동일한 에러 처리를 한다.

`try` 구문은 중첩 가능하다.

##### Exception Hierarchy

내장 예외는 다음과 같은 클래스 계층 구조를 갖는다.

- BaseException
  - SystemExit : sys.exit() 함수가 호출되는 경우 발생. 이 예외가 처리되지 않으면 프로그램이 종료된다.
  - KeyboardInterrupt : 사용자가 인터럽트 키를 누른 경우에 발생.
  - GeneratorExit : 제너레이터의 close() 메서드가 호출될 때 발생
  - Exception : 모든 내장 예외의 기본이 되는 클래스. 사용자 정의 예외를 구현할 경우 이 클래스를 상속받아야 한다.
    - StopIteration : next()나 이터레이터의 \__next__()에 대하여 더는 반환할 값이 없는 경우 발생.
    - ArithmeticError : 수치 연산 에러의 기본.
      - FloatingPointError : 부동 소수점 연산이 실패한 경우 발생. pyconfig.h에 WANT_SIGFPE_HANDLER가 정의되거나, --with-fpectl 옵션이 설정된 경우에만 발생.
      - OverflowError : 산술 연산 결과가 표현할 수 있는 범위를 벗어난 경우 발생.
      - ZeroDivisionError : 나머지 연산에서 제수가 0인 경우 발생.
    - AssertionError : Assert 구문이 실패할 경우 발생.
    - AttributeError : 속성의 참조나 할당에 실패하는 경우 발생.
    - BufferError
    - EnvironmentError : 파일 IO와 같은 파이썬 외부 에러의 기본.
      - IOError : open()과 같은 I/O 연산이 실패하는 경우 발생.
      - OSError : 시스템 관련 에러.
        - WindowsError
        - VMSError
    - EOFError : input() 계열 함수로 읽은 내용이 없이 EOF가 입력된 경우 발생.
    - ImportError : import 관련 실패 시 발생.
    - LookupError : 시퀀스 관련 에러의 기본.
      - IndexError : 시퀀스 계열 객체의 인덱스가 범위를 벗어난 경우 발생.
      - KeyError : 딕셔너리에서 키를 찾지 못한 경우에 발생
    - MemoryError : 할당할 메모리가 없을 경우 발생.
    - NameError : 유효하지 않은 이름을 접근하는 경우 발생.
      - UnboundLocalError
    - ReferenceError : 약한 참조 프록시에서 발생.
    - RuntimeError : 프로그램이 작동 중 분류할 수 없는 경우 발생.
      - NotImplementedError : 부모 클래스에 정의된 추상 메서드를 자식 클래스에서 재정의하지 않은 경우 발생.
    - SyntaxError : 구문 오류로 발생.
      - IndentationError
        - TabError
    - SystemError
    - TypeError : 부적절한 타입의 객체에 값을 할당하는 경우 발생.
    - ValueError : 타입은 올바르나 값이 적절하지 않는 경우 발생.
      - UnicodeError
        - UnicodeDecodeError
        - UnicodeEncodeError
        - UnicodeTranslateError
    - Warning
      - DeprecationWarning
      - PendingDeprecationWarning
      - RuntimeWarning
      - SyntaxWarning
      - UserWarning
      - FutureWarning
      - ImportWarning
      - UnicodeWarning
      - BytesWarning