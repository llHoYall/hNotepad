---
layout: post
title: Module - decimal
category: python
tags: python
---

&nbsp;

# Module - decimal

부동 소수점 연산의 본질적인 문제를 해결하고자 만든 모듈이다.

decimal 모듈은 float와 다르게 실수를 정확하게 표현할 수 있고, +Infinity, -Infinity, NaN을 표현할 수 있다.

decimal 모듈은 내장 수치 자료형과 동일하게 모든 수치 연산과 내장 함수의 인자로 전달이 가능하다. 또한, 내장 수치 자료형과 상호 연산도 가능하며, 내장 함수의 인자로 전달할 수도 있다.

#### Methods

- **Decimal([*value*[, *context*]])** : 정수, 문자열, 튜플, Decimal 객체를 인자로 받아서 Decimal 객체를 생성한다. 튜플을 입력할 경우 (부호(0: 양수 or 1: 음수) , 유효숫자 튜플, 소수점 자리)로 입력한다.
- **sqrt()** : 제곱근 결과를 반환한다.
- **exp()** : e ** Decimal 결과를 반환한다.
- **ln()** : Decimal의 자연로그 결과를 반환한다.
- **compare(*other*)** : 두 Decimal 객체를 비교해 그 결과를 Decimal 객체로 반환한다. 메서드 호출 객체가 더 크면 Decimal('1'), 같으면 Decimal('0'), 작으면 Decimal('-1')을 반환한다.
- **copy_abs()** : 원본의 절대값을 갖는 Decimal 객체를 반환한다.
- **copy_negate()** : 원본의 음수값을 갖는 Decimal 객체를 반환한다.
- **copy_sign(*other*)** : 원본 값에 인자의 부호를 갖는 Decimal 객체를 반환한다.
- **is_signed()** : 부호 비트가 설정돼 있으면 (즉, 음수이면) True를 반환한다.
- **is_finite()** : 유한수인 경우 True를 반환한다.
- **is_infinite()** : 무한수인 경우 True를 반환한다.
- **is_zero()** : '0' (+0, -0)인 경우 True를 반환한다.

```python
import decimal
decimal.getcontext()		# 현재 환경설정을 알려준다.
# Context(prec=28, rounding=ROUND_HALF_EVEN, Emin=-999999, Emax=999999, capitals=1, clamp=0, flags=[], traps=[InvalidOperation, DivisionByZero, Overflow])

decimal.getcontext().prec = 7		# 연산 결과가 소수점 아래 7번째 까지된다.
decimal.rounding = decimal.ROUND_CEILING		# 반올림 연산을 올림 연산으로 바꾼다.

# decimal 모듈에서 미리 정의된 환경설정
print(decimal.DefaultContext)
print(decimal.BasicContext)
print(decimal.ExtendedContext)

# 미리 정의된 환경설정을 적용
decimal.setcontext(decimal.ExtendedContext)
```

