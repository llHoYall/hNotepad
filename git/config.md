---
layout: post
title: Config
category: git
tags: git
---

&nbsp;

# Config

Git을 설정하는 명령어이다.

Git의 설정은 3단계의 scope를 갖는다.

- system : /etc/gitconfig
- global : ~/.gitconfig
- local : ~/.git/config

모든 프로젝트에 공통적으로 적용할 설정은 보통 global에 두고, 프로젝트별로 적용할 설정은 local에 둔다.

우선 순위는 local > global > system 순이다.

> $ git config **--global user.name** "*UserName*"
> $ git config **--local user.name** "*UserName*"
> - 사용자 이름을 설정한다.
>
> $ git config **--global user.email** "*E-mail*"
> $ git config **--local user.email** "*E-mail*"
> - 사용자 이메일을 설정한다.
>
> $ git config **--global push.default** *simple*
> - push할 때 기본으로 현재 branch만 하도록 한다.
>
> $ git config **--global rerere.enabled** *true*
> - reuse recorded resolution 설정이다.
>   충돌이 났을 때의 해결책들을 저장하고 있다가 동일한 문제가 발생했을 때 다시 적용해준다.
>
> $ git config **--global credential.helper** *osxkeychain*
> - 연결 암호를 저장하여 암호 입력을 하지 않아도 된다.
>   windows의 경우 osxkeychain대신 *winstore*를 사용한다.
>   *cache*를 사용하면 15분간 저장한다.
>   *store*를 사용하면 텍스트 파일로 저장한다.
>
> $ git config **--global core.autocrlf** *input*
> - 개행문자 설정이다.
>   windows의 경우 *input*대신 *true*를 써준다.
>
> $ git config **--global** <*alias_name*> <*command*>
> - Alias를 만든다.
>   Ex) $ git config --global alias.br branch
>   Ex) $ git config --global alias.cm commit
>   Ex) $ git config --global alias.co checkout
>   Ex) $ git config --global alias.st status
>   Ex) $ git config --global alias.unstage 'reset HEAD --'
>   Ex) $ git config --global alias.last 'log -1 HEAD'
>   Ex) $ git config --global alias.visual '!gitk'
>
> $ git config **--global core.editor** *vim*
> - 환경변수에 설정한 편집기 대신 명시한 편집기를 사용한다.
>
> $ git config **--global merge.tool** *p4merge*
> - Merge 도구를 선택한다.
>
> $ git config **--global help.autocorrect** *1*
> - 명령어를 잘못 입력해도 자동으로 추측하여 실행해준다.
>
> $ git config **--global color.ui** *true*
> - 터미널 출력 결과에 색상을 입힌다.
> - **color.branch** <*true/false/always*>
> - **color.diff** <*true/false/always*>
> - **color.interactive** <*true/false/always*>
> - **color.status** <*true/false/always*>
>
> $ git config **--global pull.rebase** *true*
> - pull 명령어에 기본적으로 --rebase 옵션이 적용되도록 한다.  
>
> $ git config **--global commit.template** <*file*>
> - Commit 시, 명시한 파일에 있는 내용을 자동으로 넣는다.
>
> $ git config **--list**
> - 설정된 내용을 보여준다.

