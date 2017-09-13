---
layout: post
title: Terminal Output
category: shell
tags: [shell, bash]
---

&nbsp;

# Terminal Output

echo 명령어를 사용하면 터미널에 출력을 할 수 있다.

```sh
echo "Hello World!"
```

&nbsp;

## 개행하지 않기

echo 명령을 사용하면 기본적으로 자동으로 개행을 한다.

이것을 막으려면 **\-n** 옵션을 사용한다.

~~~sh
echo -n "We are "
echo "the same line."
~~~

&nbsp;

## 색깔 입히기

echo 명령에 **\-e** 옵션을 사용하면 색깔입히기가 가능하다.

단, color 적용이 가능한 터미널이어야만 한다.

<Tested on MAC - iTerm2>

다음의 형식을 사용하여 적용을 한다.

> \033[##m

\##  부분은 숫자가 들어가며 각각의 의미는 다음과 같다.

- 0 - 적용 종료
- 1 - Bold
- 2 - Dark
- 3 - Italic
- 4 - Underline
- 5 - Blink
- 7 - Foreground/Backgound color reverse
- 8 - Hidden
- 9 - Strike out
- 30 - Foreground black
- 31 - Foreground red
- 32 - Foreground green
- 33 - Foreground yellow
- 34 - Foreground blue
- 35 - Foreground magenta
- 36 - Foreground cyan
- 37 - Foreground - white
- 40 - Background black
- 41 - Background red
- 42 - Background green
- 43 - Background yellow
- 44 - Background blue
- 45 - Background magenta
- 46 - Background cyan
- 47 - Background - white

~~~sh
echo -e "\033[31m Test String \033[0m"
echo -e "\033[43m Test String \033[0m"
echo -e "\033[44;35m Test String \033[0m"
~~~

&nbsp;

## Quotation Mark

Single quote 혹은 Double quote 를 사용하여 문자열을 출력할 수 있다.

문자열 연결도 가능하며, 섞어쓸 수도 있다.

- single quote를 출력하고 싶으면 **\'**를 사용한다.
- Single quote 안에서 double quote를 출력하고 싶으면 그냥 사용한다.
- Double quote 안에서 double quote를 출력하고 싶으면 **\"**를 사용한다.
- Double quote 안에서 single quote를 출력하고 싶으면 그냥 사용한다.

~~~sh
echo 'Hello' 'World'
echo 'Hello' "World"
echo 'I'\''m a boy.'
echo 'I said, "Hello".'
echo "You're a girl."
echo "You said, \"Hello\"."
~~~

&nbsp;

## Here Document

다음과 같은 형식을 사용한다.

> {*command*} << {*exit string*}
> body
> {*exit string*}

exit string은 따로 정해진 것 없이 임의의 문자열을 사용하면 된다.

exit string에 single quote를 붙이면 변수 확장이 일어나지 않는다.

exit string을 그냥 사용하면 변수 확장이 일어나며, 이를 막으려면 변수에 backslash를 붙인다.

~~~sh
str="test"

cat << 'END'
$str			# $str
`echo abc`		# `echo abc`
END

cat << EOT
$str			# test
\$str			# $str
`echo abc`		# abc
\`echo abc\`	# `echo abc`
EOT
~~~

&nbsp;

## Here String

다음과 같은 형식을 사용한다.

> {*command*} <<< {' or "}{*exit string*}
> body
> {' or "}

Single quote를 사용하면 변수 확장이 일어나지 않는다.

Double quote를 사용하면 변수 확장이 일어나며, 이를 막으려면 변수에 backslash를 붙인다.

~~~sh
str="test"

cat <<< '$str	# $str
`echo abc`'		# `echo abc`

cat <<< "$str	# test
\$str			# $str
`echo abc`		# abc
\`echo abc\`"	# `echo abc`
~~~

