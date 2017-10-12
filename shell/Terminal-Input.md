---
layout: post
title: Terminal Input
category: shell
tags: [shell, bash]
---

&nbsp;

# Terminal Input

## 사용자 입력 받기

read 명령어로 사용자 입력을 받을 수 있다.

```sh
read id
```

명령어 뒤에 명시한 변수에 사용자 입력이 저장된다.

&nbsp;

## 1 문자 입력받기

다음과 같은 방법을 사용하면 1개의 문자만 입력받을 수 있다.

```sh
tty_state=$(stty -g)    # backup terminal settings
stty raw    # change terminal mode to raw
input=$(dd bs=1 count=1 2> /dev/null)
stty "$tty_state"    # restore terminal settings
```

stty는 터미널 세팅을 위한 명령어이다. -g 옵션을 사용하면 현재 설정을 디스플레이한다.

dd는 standard input을 standard output으로 복사하는 명령어이다. bs 옵션은 block size를 의미하며 byte 단위이다. count 옵션은 몇 개의 block을 복사할 것인지를 명시한다.

2> /dev/null은 standard error를 /dev/null로 redirection한다.

&nbsp;

## 사용자 입력 숨김상태로 받기

다음과 같이 터미널의 세팅을 변경하여 사용자의 입력을 숨길 수 있다.

```sh
stty -echo    # echo back off
stty echo    # echo back on
```

Echo back을 하지 않으면 사용자의 입력이 출력으로 보이지 않으므로 숨길 수 있게된다.

&nbsp;

## 사용자 입력 메뉴

다음의 코드는 메뉴를 사용하는 예이다.

```sh
while :
do
	echo "1) list file"
	echo "2) show current directory"
	echo "3) exit"
	echo -n "Input menu: "
	read menu

	case $menu in
		1)
			ls
			;;
		2)
			pwd
			;;
		3)
			exit
			;;
		*)
			echo "Error: Unknown command"
	esac
	echo
done
```

&nbsp;

## 파일 읽으면서 사용자 입력 받기

다음은 file.txt 파일로부터 한 줄씩 읽고 출력을 하면서, 사용자로부터 디렉토리를 입력받아 해당 디렉토리의 목록을 출력하는 코드이다.

```sh
tty=`tty`    # command substitution (execution result)
while read filebuf    # read one-line from file
do
	echo $filebuf
	read dir < $tty
	echo "Command: ls $dir"
	ls $dir
done < file.txt
```

\`command\`는 해당 명령을 실행하여 결과를 받는다.

