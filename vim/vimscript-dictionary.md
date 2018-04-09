---
layout: post
title: VimScript - Dictionary
category: vim
tags: [vim, dictionary]
---

# VimScript - Dictionaries

## Dictionaries

딕셔너리는 `{}` 기호로 나타낸다. 값은 heterogeneous이며, 키는 문자열이어야 한다. 키가 문자열이 아닐 경우 자동으로 변환된다.

```vim
echo {'a': 1, 'b': 'foo'}
echo {'a': 1, 100: 'foo'}
>>> {'a': 1, '100': 'foo'}
```

## Indexing

```vim
echo {'a': 1, 100: 'foo'}['a']
>>> 1
echo {'a': 1, 100: 'foo'}.a
>>> 1
```

## Assigning and Adding

```vim
let foo = {'a': 1}
let foo.a = 100
let foo.b = 200
echo foo
>>> {'a': 100, 'b': 200}
```

## Removing

`remove`와 `unlet`의 두 가지 방법이 있다. `remove`는 `unlet`을 대체할 수 있지만, 반대는 안된다. 따라서 `remove`를 사용하는 것이 통일성을 줄 수 있다.

```vim
let foo = {'a': 100, 'b': 200}
let test = remove(foo, 'a')
echo test
>>> 100
unlet foo.b
echo foo
>>> {}
```

## Dictionary Functions

```vim
echom get({'a': 100}, 'a', 'default')
>>> 100
echom get({'a': 100}, 'b', 'default')
>>> default

echom has_key({'a': 100}, 'a')
>>> 1
echom has_key({'a': 100}, 'b')
>>> 0

echo items({'a': 100, 'b': 200})
>>> [['a', 100], ['b', 200]]
```

