---
layout: post
title: VimScript - List
category: vim
tags: [vim, list]
---

# VimScript - Lists

## Lists

리스트는 `[]` 기호로 나타내며, `,`로 구분된다. 또한 중첩이 가능하다.

```vim
echo ['hello', 1, 'world']
echo ['hello', [1, 'world']]
```

## Indexing

리스트는 zero-indexed이며, negative indexing이 가능하다.

```vim
echo [0, [1, 2]][1]
>>> [1, 2]
echo [0, [1, 2]][-2]
>>> 0
```

## Slicing

```vim
echo ['a', 'b', 'c', 'd', 'e'][0:2]
>>> ['a', 'b', 'c']
echo ['a', 'b', 'c', 'd', 'e'][-2:-1]
>>> ['d', 'e']
echo ['a', 'b', 'c', 'd', 'e'][:1]
>>> ['a', 'b']
echo ['a', 'b', 'c', 'd', 'e'][3:]
>>> ['d'. 'e']
echo "abcd"[0:2]
>>> abc
```

## Concatenation

리스트는 `+`로 연결할 수 있다.

```vim
echo ['a', 'b'] + ['c']
>>> ['a', 'b', 'c']
```

## List Functions

```
let foo = ['a']
echo add(foo, 'b')
>>> ['a', 'b']

echo len(foo)
>>> 2

echo get(foo, 0, 'default')
>>> a
echo get(foo, 100, 'default')
>>> default

echo index(foo, 'b')
>>> 1
echo index(foo, 'nope')
>>> -1

echo join(foo)
>>> a b
echo join(foo, '---')
>>> a---b
echo join([1, 2, 3], '')
>>> 123

echo reverse(foo)
>>> ['b', 'a']

echo sort(foo)
>>> ['a', 'b']

let bar = ['c', 'd']
echo extend(foo, bar)
>>> ['a', 'b', c', 'd']
```

