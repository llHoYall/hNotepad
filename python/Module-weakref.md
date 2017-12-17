---
layout: post
title: Module - weakref
category: python
tags: python
---

&nbsp;

# Module - weakref

weakref 모듈은 객체에 대한 약한 참조를 만드는 데 사용한다. 약한 참조는 변수가 객체를 참조할 때, 레퍼런스 카운터를 증가 시키지 않고 참조하는 객체를 얻을 수 있다.

리스트나 딕셔너리 같은 내장 데이터 타입에 대해 약한 참조 객체를 만드려면 subclassing을 해야한다.

모든 객체가 약한 참조 객체를 생성할 수 있는 것은 아니다. 현재 지원가능한 객체는 클래스 인스턴스, 파이썬 함수, 인스턴스 메서드, sets, frozensets, 파일 객체, 생성자, 타입 객체, basddb 모듈의 DBCursor, 소켓, arrays, dequeue, 정규식 패턴 객체이다.

#### Methods

- **ref(*object*[, *callback*])** : 객체에 대한 약한 참조 객체를 반환한다. 객체가 메모리에 존재하는 경우 객체에 대한 참조를 반환하며, 그렇지 않은 경우 None을 반환한다.
- **proxy(*object*[, *callback*])** : 객체에 대한 약한 참조 프록시를 생성한다. 명시적으로 약한 참조 객체를 생성하는 대신 프록시를 이용해 객체의 참조를 얻을 수 있다.
- **getweakrefcount(*object*)** : 객체에 대한 약한 레퍼런스 카운터를 반환한다.
- **getweakrefs(*object*)** : 객체를 참조하는 약한 참조 객체와 프록시를 리스트로 반환한다.

----

weak dictionary는 구성 요소인 키와 값 중 하나가 약한 참조로 구성되어 있는 경우이다. 예를 들어 각 객체에 ID를 키로 부여해 dictionary에 넣어서 관리하는 경우 dictionary에 넣는 순간 레퍼런스 카운터가 하나 증가한다. 반면 weak dictionary의 경우 사용자가 dictionary에 입력해도 레퍼런스 카운터가 증가되지 않으며, 원본 객체가 삭제되면 자동적으로 dictionary의 객체도 삭제되어 None이 된다.

### WeakKeyDictionary Class

#### Methods

- **WeakKeyDictionary([*dict*])** : 키를 약한 참조로 갖는 dictionary 객체를 생성한다.

### WeakValueDictionary Class

#### Methods

- **WeakValueDictionary([*dict*])** : 값을 약한 참조로 갖는 dictionary 객체를 생성한다.

```python
# ObjectManager.py
import weakref

class ObjectMAnager:
    def __init__(self):
        self.weakDict = weakref.WeakValueDictionary()
        
    def InputObject(self, obj):
        objectID = id(obj)
        self.weakDict[objectID] = obj
        return objectID
    
 	def GetObject(self, objectID):
        try:
            return self.weakDict[objectID]
        except:
            return None
        
# Example
from ObjectManager import *

class Apple:
    pass
red_apple = Apple()
red_apple.color = "red"

objManager = ObjectManager()
red_id = objManager.InputObject(red_apple)
objManager.GetObject(red_id).color

del red_apple
objManager.GetObject(red_id)
```

