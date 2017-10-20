---
layout: post
title: Register
category: vim
tags: vim
---

&nbsp;

# Register

Unix, Mac, Linux 에서는 **~/.viminfo**, Windows 에서는 **~/_viminfo** 파일에 레지스터의 내용을 저장한다.

&nbsp;

### 레지스터 명령

**"** 기호를 사용하여 레지스터를 명시한다. 예를 들어, `"3p` 명령은 3번 레지스터의 내용을 붙여넣는다.

- :reg[ister] - 현재 사용중인 레지스터 목록을 보여준다.
- :reg[ister] {*reg*} - 명시한 레지스터의 내용을 보여준다. `:reg a` 혹은 `:reg "a`, `:reg ab`와 같이 사용한다.
- {*reg*}y{*motion*} - 명시한 레지스터에 motion에 해당하는 내용을 복사하여 넣는다.
- {*reg*}p - 명시한 레지스터의 내용을 현재 커서 뒤쪽에 붙여넣는다. 개행 문자가 포함되어 있다면 아래 라인에 붙여넣는다.
- {*reg*}P - 명시한 레지스터의 내용을 현재 커서 앞쪽에 붙여넣는다. 개행 문자가 포함되어 있다면 위 라인에 붙여넣는다.
- {*reg*}d{*motion*} - 명시한 레지스터에 motion에 해당하는 내용을 삭제하여 넣는다.
- \<CTRL-r>{*reg*} - 명시한 레지스터의 내용을 붙여 넣는다. I-Mode에서만 작동한다. 레지스터를 명시하지 않을경우, "레지스터를 사용한다.

&nbsp;

### 레지스터 종류

##### Unnamed Register

- " : 가장 최근에 복사, 삭제된 내용.

##### Numberd Register

- 0 : 가장 최근에 복사된 내용.
- 1 ~ 9 : 최근에 삭제된 내용. 시간순으로 저장되며 1번이 가장 최근.

##### Small Delete Register

- \- : 가장 최근에 한 라인 이내로 삭제된 내용.

##### Named Register

- a ~ z : 사용자가 지정하여 사용할 수 있는 레지스터. 새로운 내용으로 덮어쓴다.
- A ~ Z : 사용자가 지정하여 사용할 수 있는 레지스터. 새로운 내용을 뒤에 덧붙인다.

##### Read-Only Register

- : : 가장 최근에 C-Mode에서 사용한 명령.
- . : 가장 최근에 I-Mode에서 입력한 내용.
- % : 현재 편집 중인 파일명.

##### Alternate Buffer Register

- \# : 이전에 열였던 파일명.

##### Expression Register

- = : 직접적인 내용이 들어있는 레지스터가 아니고, 수식 표현등을 사용하여 결과값을 저장할 수 있는 레지스터이다.

##### Selection and Drop Register

- \* :
- \+ : 
- ~ : 

##### Black Hole Register

- _ : 이 레지스터를 이용하면 다른 레지스터의 내용을 건드리지 않고 작업을 할 수 있다. 예를 들면, 삭제한 내용을 이 레지스터에 넣으면 다른 레지스터에 있는 삭제된 내용은 그대로 유지된다. 이 레지스터를 읽어도 아무 것도 반환되지 않는다.

##### Last Search Pattern Register

- / : 가장 최근에 검색한 내용.