---
layout: post
title: Class
category: python
tags: python
---

&nbsp;

# Class

클래스는 다음의 문법으로 정의한다.

```python
class name:
    # Memvber Variables
    # Member Methods
```

클래스 객체는 독립적인 namespace를 갖는다. 클래스 인스턴스도 각각 독립적인 namespace를 갖는다. 변수나 함수 이름을 찾을 때 인스턴스 객체 -> 클래스 객체 -> 전역 순으로 찾는다.

파이썬에서는 클래스에 대한 기본 접근 권한을 public으로 한다.

파이썬에서는 런타임에 클래스나 인스턴스에 멤버 변수를 추가, 삭제할 수 있다.

##### 생성자 & 소멸자

생성자, 소멸자는 각각 `__init__()`, `__del__()` 함수로 정의되어 있다. 변경을 원하면 재정의하면 된다.

생성자는 인스턴스가 생성될 때 호출되며, 소멸자는 인스턴스의 레퍼런스 카운터가 0이 될 때 호출된다.