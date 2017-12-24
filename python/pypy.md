---
layout: post
title: pypy
category: python
tags: python
---

&nbsp;

# pypy

pypy는 파이썬으로 만든 파이썬이다. 보통 python이라고 하면 C로 구현된 CPython을 의미한다. pypy의 목표는 CPython보다 빠르지만, Cpython과 완벽하게 호환되게 하는 것이다.

pypy는 interpreter와 translator로 구성되어 있다.

Interpreter는 파이썬 코드를 정적 타입으로 컴파일이 가능하도록 제약을 가한 파이썬의 서브셋인 RPython (Restricted Python) 으로 만들어져 있다.

Translator는 RPython 코드를 분석해 C나 자바 바이트코드 같은 하위 언어로 변환시켜준다. 또한, JIT generator가 포함되어 있다. JIT (Just-In Time) 컴파일러는 프로그램 동작 중 코드를 바로 기계어로 변경해 런타임으로 동작하는 프로그램의 성능을 높이는 기술이다. pypy에서는 RPython 코드를 분석해 JIT generator가 자동으로 인터프리터에 tracing-JIT 컴파일러를 넣어 준다.

pypy는 CPython보다 적은 메모리를 사용하고, 스레드를 많이 사용하는 프로그램에서 마이크로 스레드 간의 복잡하고 성능이 느려지는 문제를 해결한 stackless 파이썬을 지원한다. 또, 믿을 수 없는 코드를 안전하게 실행해 볼 수 있는 sandboxing 기능을 프로토타입 단계지만 지원한다.

### Reference

- http://pypy.org/