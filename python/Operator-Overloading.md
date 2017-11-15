---
layout: post
title: Operator Overloading
category: python
tags: python
---

&nbsp;

# Operator Overloading

이미 존재하는 연산자를 개발하고자 하는 도메인에 맞춰 변경을 할 수 있다.

- **\__add__(*self*, *other*)** : +(이항)
  Ex : A + B, A += B

- **\__sub__(*self*, *other*)** : -(이항)
  Ex : A - B, A -= B

- **\__mul__(*self*, *other*)** : *
  Ex : A * B, A *= B

- **\__truediv__(*self*, *other*)** : /
  Ex : A / B, A /= B

- **\__floordiv__(*self*, *other*)** : //
  Ex : A // B, A //= B

- **\__mod__(*self*, *other*)** : %, 
  Ex : A % B, A %= B

- **\__divmod__(*self*, *other*)** : divmod()
  Ex : divmod(A, B)

- **\__pow__(*self*, *other*[, *modulo*])** : pow(), \*\*
  Ex : pow(A, B), A \*\* B

- **\__lshift__(*self*, *other*)** : <<
  Ex : A << B, A <<= B

- **\__rshift__(*self*, *other*)** : >>
  Ex : A >> B, A >>= B

- **\__and__(*self*, *other*)** : &
  Ex : A & B, A &= B

- **\__xor__(*self*, *other*)** : ^
  Ex : A ^ B, A ^= B

- **\__or__(*self*, *other*)** : |
  Ex : A | B, A |= B

- **\__abs__(*self*)** : abs()
  Ex : abs(A)

- **\__pos__(*self*)** : +(단항)
  Ex : +A

- **\__neg__(*self*)** : -(단항)
  Ex : -A

- **\__invert__(*self*)** : ~
  Ex : ~A (bitwise)

다음은 기본 연산자와 동작 구분을 위한 확장 연산자이다.

- **\__iadd__(*self*, *other*)** : +=
  Ex : A += B

- **\__isub__(*self*, *other*)** : -=
  Ex : A -= B

- **\__imul__(*self*, *other*)** : *=
  Ex : A *= B

- **\__itruediv__(*self*, *other*)** : /=
  Ex : A /= B

- **\__ifloordiv__(*self*, *other*)** : //=
  Ex : A //= B

- **\__imod__(*self*, *other*)** : %=
  Ex : A %= B

- **\__ipow__(*self*, *other*)** : \**=
  Ex : A \**= B

- **\__ilshift__(*self*, *other*)** : <<=
  Ex : A <<= B

- **\__irshift__(*self*, *other*)** : >>=
  Ex : A >>= B

- **\__iand__(*self*, *other*)** : &=
  Ex : A &= B

- **\__ior__(*self*, *other*)** : |=
  Ex : A |= B

- **\__ixor__(*self*, *other*)** : ^=
  Ex : A ^= B

피연산자의 위치가 바뀌면 호출되는 메서드도 바뀐다.

- **\__radd__(*self*, *other*)** : +
  Ex : B + A

- **\__rsub__(*self*, *other*)** : -
  Ex : B - A

- **\__rmul__(*self*, *other*)** : *
  Ex : B * A

- **\__rtruediv__(*self*, *other*)** : /
  Ex : B / A

- **\__rfloordiv__(*self*, *other*)** : //
  Ex : B // A

- **\__rmod__(*self*, *other*)** : %
  Ex : B % A

- **\__rdivmod__(*self*, *other*)** : divmod()
  Ex : divmod(B, A)

- **\__rpow__(*self*, *other*)** : **
  Ex : B ** A

- **\__rlshift__(*self*, *other*)** : <<
  Ex : B << A

- **\__rrshift__(*self*, *other*)** : >>
  Ex : B >> A

- **\__rand__(*self*)** : &
  Ex : B & A

- **\__ror__(*self*)** : |
  Ex : B | A

- **\__rxor__(*self*)** : ^
  Ex : B ^ A

비교 연산자에 해당하는 메서드는 다음과 같다.

- **\__lt__(*self*, *other*)** : <
  Ex : A < B, B > A

- **\__le__(*self*, *other*)** : <=
  Ex : A <= B, B >= A

- **\__eq__(*self*, *other*)** : ==
  Ex : A == B, B == A

- **\__ne__(*self*, *other*)** : !=
  Ex : A != B, B != A

- **\__ge__(*self*, *other*)** : >=
  Ex : A >= B, B <= A

- **\__gt__(*self*, *other*)** : >
  Ex : A > B, B < A

시퀀스 객체를 위한 연산자 다중 메서드는 다음과 같다.

- **\__len__(*self*)** : len()
  Ex : len(A)

- **\__contain__(*self*, *item*)** : in
  Ex : item in A

- **\__getitem__(*self*, *key*)** : A[key]
  Ex : A[key], for 문

- **\__setitem__(*self*, *key*, *value*)** : A[key] = value
  Ex : A[key] = value

- **\__delitem__(*self*, *key*)** : del A[key]
  Ex : del A[key]

