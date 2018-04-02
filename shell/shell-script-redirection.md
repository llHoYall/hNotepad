---
layout: post
title: Shell Script - Redirection
category: shell
tags: [bash, script]
---

# Shell Script - Redirection

#### `>`, `>>`

​	Stdout을 redirection한다.  `>`은 덮어쓰지만, `>>`은 추가한다.

```bash
$ echo "hello" > /dev/null

$ echo "world" >> ./hello.txt
```

#### `<`, `<<<`

​	Stdin을 redirection한다.

```bash
$ cat < ./hello.txt

$ cat <<< "User name is $USER"
```

#### `2>`, `2>>`

​	Stderr를 redirection한다. `2>`은 덮어쓰지만, `2>>`은 추가한다.

#### `&>`

​	Stdout, Stderr를 모두 redirection한다.

#### `1>&2`, `2>&1`

​	`1>&2`는 Stdout을 Stderr로 보내고, `2>&1`은 Stderr를 Stdout으로 보낸다.

#### `<<EOF ~~ EOF`

​	heredoc이다. 여러 줄의 문자열을 Stdin으로 redrection한다.

```bash
cat > ./hello.txt <<EOF
Hello World
Host name is $(hostname)
User name is $USER
EOF
```

