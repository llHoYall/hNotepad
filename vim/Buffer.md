---
layout: post
title: Buffer
category: vim
tags: vim
---

&nbsp;

# Buffer

vim에서 현재 작업중인 문서를 버퍼라고 한다. 연결된 파일이 있다면 `파일=버퍼`로 볼 수도 있다. 빈 문서로 시작을 했다면 파일과 연결되지 않은 버퍼만 있는 상태이다.

&nbsp;

### 버퍼 목록 보기

- :ls
  :buffers
  :files

위 명령을 입력하면 현재 작업중인 버퍼 목록이 나타나며, 특수 기호로 현재 버퍼의 상태를 나타낸다.

- % : 현재 편집 중인 버퍼.
- \# : 직전에 열었던 버퍼 혹은 다음에 열 버퍼. \<CTRL-^>명령어를 사용하면 #이 붙은 버퍼가 열린다.
- a : 활성화된 버퍼. 즉, 현재 화면에 보이는 버퍼.
- \+ : 변경된 부분이 있는 버퍼.


&nbsp;

### 버퍼 목록 이동

버퍼 사이를 이동하기 전에 수정된 내용은 저장해야 한다. 강제로 이동하려면 !를 붙인다.

- \<CTRL-^>
  :e # - 이전에 열었던 파일을 연다. #은 숫자가 아니라 sharp 기호이다.
- {#}\<CTRL-^>
  :e #{#} - #번째 파일 목록을 연다.
- :[#]n - 숫자만큼 다음 파일을 연다. 숫자 생략 시 1.
- :[#]N - 숫자만큼 이전 파일을 연다. 숫자 생략 시 1.

&nbsp;

### 버퍼 목록에 파일 추가

- :n {*pattern*} - 패턴에 해당하는 파일을 목록에 추가하고 첫 번째 파일을 연다.

예를 들면 다음과 같이 사용한다.

> :n *.txt			// 모든 txt 파일
>
> :n \*\*/*.txt		// 하위 디렉토리를 포함하여 모든 txt 파일
>
> :n doc\*\*/*.txt	// doc으로 시작하는 디렉토리 내의 모든 txt 파일

&nbsp;

### 버퍼 목록에서 파일 제거

- :0f[ile] - 현재 버퍼를 목록에서 제거한다. 연결된 파일이 있다면 해제하여 [No Name] 버퍼로 만든다.

