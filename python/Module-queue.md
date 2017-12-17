---
layout: post
title: Module - queue
category: python
tags: python
---

&nbsp;

# Module - queue

파이썬 에서는 queue 모듈에서 Queue, PriorityQueue, LifoQueue를 제공한다.

queue 모듈은 thread 환경을 고려했기 때문에 여러 thread가 동시에 큐 객체의 데이터를 사용해도 정상 동작을 보장한다.

각 클래스는 동일한 메서드를 갖고 있으며 해당 클래스의 정렬 방식에 따라 get 계열 메서드의 결과만 다르다. (FIFO, LIFO, Priority FIFO)

큐 객체를 생성할 때 명시적으로 크기를 지정할 수 있다. 이 때, 큐 객체에 아이템이 없는 상태에서 get()을 호출하거나, 아이템이 꽉 찬 상태에서 put()을 호출할 경우 큐 객체가 blocking 된다. 즉, 다른 스레드에서 해당 큐 객체에 아이템을 넣거나 뺄 때까지 무한 대기상태에 빠진다.

----

### Queue Class

#### Methods

- **Queue(*maxsize*)** : FIFO 큐 객체를 생성한다.
- **qsize()** : 큐 객체에 입력된 아이템의 개수를 반환한다.
- **put(*item*[, *block*[, *timeout*]])** : 큐 객체에 아이템을 입력한다.
- **put_nowait(*item*)** : blocking 없이 큐 객체에 아이템을 입력한다. 큐 객체가 꽉 차있는 경우 queue.Full 예외를 발생한다.
- **get([*block*[, *timeout*]])** : 생성된 큐 객체 특성에 맞춰 아이템 1개를 반환한다. block은 boolean으로 블로킹 여부를, timeout은 blocking이 될 시간을 초단위로 입력받는다.
- **get_nowait()** : blocking 없이 큐 객체에 들어있는 아이템을 반환한다. 큐 객체가 비어있는 경우 queue.Empty 예외를 발생한다.

----

### LifoQueue Class

#### Methods

- **LifoQueue(*maxsize*)** : 스택이라 불리는 LIFO 큐 객체를 생성한다.

----

### PriorityQueue Class

#### Methods

- **PriorityQueue(*maxsize*)** : 우선순위 큐 객체를 생성한다. 입력되는 아이템 형식은 (순위, 아이템)의 튜플로 입력되며, 우선순위는 숫자가 작을수록 순위가 높다.

----

