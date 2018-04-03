---
layout: post
title: VimScript - Control
category: vim
tags: [vim, lists]
---

# VimScript - Control Statement

## if conditionals

if 조건문은 0이 아닌 정수는 true로 그 외는 false로 처리된다. if 조건문의 문법은 다음과 같다.

```vim
if <condition>
	<statements>
elseif <condition>
	<statements>
else
	<statements>
endif
```

statements들은 `|`(pipe character)로 한 줄로 연결할 수 있다.

condition에서 숫자 1은 true, 0은 false로 처리된다. 숫자로 시작하는 문자열은 해당 숫자로 처리되며, 숫자로 시작하지 않는 문자열은  0으로 처리된다.

조건식에서 비교를 할 때, 숫자는 상관이 없지만 문자열의 경우는 주의해야할 점이 있다.

- `==` : 문자열 비교 시, 사용자 설정에 따라 case-sensitivity 여부가 결정된다.
- `==?` : 문자열 비교 시, case-insensitive 비교를 한다.
- `==#` : 문자열 비교 시, case-sensitive 비교를 한다.

## for loops

for 반복문의 문법은 다음과 같다.

```vim
for <variable> in <list expression>
	<statements>
endfor
```

​	사용 예)

```vim
let c = 0
for i in [1, 2, 3, 4]
	let c += i
endfor
echom c
>>> 10
```

## while loops

while 반복문의 문법은 다음과 같다. `<CTRL-c>`를 누르면 강제로 종료할 수 있다.

```vim
while <condition>
	<statements>
	[continue]
	[break]
endwhile
```

​	사용 예)

```vim
let c = 1
let total = 0
while c <= 4
	let total += c
	let c += 1
endwhile
echom total
>>> 10
```

