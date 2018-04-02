---
layout: post
title: Shell Script - Variable
category: shell
tags: [bash, script]
---

# Shell Script - Variable

#### ` $ `  

​	변수를 나타낸다. 변수에서 값을 얻어올 때 이 기호를 사용한다.

```bash
hello="hello world"
echo $hello
```

#### `$()`, ` `` `

​	`()`, ` `` `안의 명령을 실행하여 결과를 변수처럼 사용한다. 

```bash
sudo docker rm $(docker ps -aq)
echo $(date)

sudo docker rm `docker ps -aq`
echo `date`
```

#### `''`

​	문자열을 나타낸다. 변수, $(), `` 등도 처리되지 않고 문자 그대로 사용된다.

​	Double quotes를 사용하려면 escaping 한다.

```bash
echo '$USER'
# $USER

bash -c "/bin/echo '{\"user\": \"$USER\"}'"
```

#### `""`

​	문자열을 나타낸다. 변수, $(), ``등도 처리된다. 처리하지 않으려면 escaping 한다.

```bash
echo "Hello World"
echo "$USER"
# HoYa
echo "Host name is $(hostname)"
echo "Time: `date`"
echo "\$hello \" \`"
# $hello " `
```

#### `"''"`

​	명령 안에서 다시 명령을 실행하고 매개 변수를 지정할 때 사용한다.

```bash
bash -c "/bin/echo Hello 'World'"
```

#### `${}`

​	변수 치환이다. "" 문자열 안에서 변수를 출력할 때 주로 사용한다. $만 사용해도 된다.

​	스크립트에서 변수의 기본 값을 설정할 때도 사용한다.

```bash
str="World"
echo "Hello ${str}"

HELLO=
HELLO=${HELLO-"abcd"}
echo $HELLO
# 변수가 있으면 그대로 사용하고, 변수가 없으면 기본 값을 대입한다.
# 즉, 결과는 NULL

WORLD=
WORLD=${WORLD:-"abcd"}
echo $WORLD
# 변수에 값이 있으면 그대로 사용하고, NULL이면 기본 값을 대입한다.
# 즉, 결과는 abcd
```

#### `{start..end}`

​	연속된 숫자를 표현한다.

```bash
echo {1..10}
# 1 2 3 4 5 6 7 8 9 10
```

#### `export`

​	설정한 값을 환경 변수로 만든다.

```bash
export str="Hello"
```

