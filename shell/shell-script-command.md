---
layout: post
title: Shell Script - Command
category: shell
tags: [bash, script]
---

# Shell Script - Command



#### `;`

​	여러 명령을 한 줄로 실행한다. 앞에 있는 명령이 실패해도 뒤에 있는 명령이 실행된다.

```bash
false; echo "hello"
```

#### `|`

​	여러 명령을 동시에 실행한다. 앞의 명령의 stdout을 뒤의 명령의 stdin으로 보낸다. 

​	pipe로 연결된 명령들은 process group을 형성한다.

```bash
$ ls -al | grep .txt
```

#### `&&`

​	여러 명령을 한 줄로 실행한다. 앞에 있는 명령이 에러 없이 실행되야 뒤에 있는 명령이 실행된다.

```bash
make && make install
```

#### `\`

​	긴 명령을 여러 줄로 표현할 때, 각 줄의 끝에 붙여 사용한다.

#### `{str,str}`

​	한 번의 명령으로 여러 문자열을 처리한다.

```bash
cp ./{hello.txt,world.txt} hello-dir/
```

#### `printf`

​	지정한 형식대로 값을 출력한다.

```bash
printf 80\\nexampleuser\\ny | example-config
# example-config는 사용자에게 Port, User, Save Config를 입력받는 프로그램이라고 하자.
# printf로 값을 미리 설정하여 파이프로 example-config에게 넘겨주면 자동으로 값이 입력된다.
# \\n은 개행이다.
```

#### `sed`

​	문자열을 변경한다.

```bash
sed -i "s/hello/world/g" hello.txt
# hello.txt 파일에서 hello를 world로 변경한다.
```

