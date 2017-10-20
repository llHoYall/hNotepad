---
layout: post
title: Command Line
category: vim
tags: vim
---

&nbsp;

# Command Line

## 명령행 인자

- \-
  Standard input을 의미
- \--
  이 옵션 뒤로는 옵션이 존재하지 않음을 의미. 즉, 이 옵션 뒤로 나오는 문자열은 모두 실행 인자로 처리한다. 

&nbsp;

## 여러 명령어를 동시에 실행

- Semi-Colon (;)
  첫 번째 명령이 실패해도 두 번째 명령이 실행된다.
- Double Vertial Bar (||)
  첫 번째 명령이 실패해도 두 번째 명령이 실행된다.
- Double Ampersand (&&)
  첫 번째 명령이 성공할 때만 두 번째 명령이 실행된다.
- Pipe (|)
  첫 번째 명령의 결과를 두 번째 명령에서 사용한다.

&nbsp;

## 사용 예

> $ ps -ef | vim -

현재 프로세스의 상태를 출력. 이 출력을 입력으로 받아 vim을 실행.

