---
layout: post
title: Shell Script - Control
category: shell
tags: [bash, script]
---

# Shell Script - Control Flow Statements

#### `if`

​	if 조건문이다.

 - 숫자 비교

   - `-eq`
   - `-ne`
   - `-gt`
   - `-ge`
   - `-lt`
   - `-le`

- 문자열 비교

  - `=`, `==` : 문자열이 같으면 true.
  - `!=`
  - `-z` : 문자열이 null이면 true. 
  - `-n` : 문자열이 null이 아니면 true.


```bash
if [ $a -eq $b ]; then
	echo $a
fi
```

#### `for`

​	for 반복문이다.

```bash
for i in $(ls)
do
	echo $i
done

for (( i=0; i < 10; i++ ))
do
	echo $i
done

NUM=(1 2 3)
for i in ${NUM[@]}
do
	echo $i
done
```

#### `while`

​	while 반복문이다.

```bash
while :
do
	echo 'Hello World";
	sleep 1;
done
```

