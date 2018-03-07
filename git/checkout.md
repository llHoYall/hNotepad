---
layout: post
title: Checkout
category: git
tags: git
---



# Checkout

Branch를 변경하고 working directory의 파일을 교체하는 명령어이다.

> $ git checkout <*branch*>
> - HEAD 포인터가 명시한 branch를 가리킨다.
>
> $ git checkout <*commit*>
> - 특정 commit을 checkout하고, detached HEAD 상태가 된다.
>
> $ git checkout HEAD <*filename*>
>
> - Working directory에서 변경된 부분을 버린다.
>
> $ git checkout **-b** <*branch*>
> - -b 옵션을 추가하면 branch 명령어도 수행한다.
>  즉, branch 명령어 처리 후 checkout 명령어를 처리한다.
>
> $ git checkout **-b** <*new_branch*> <*branch_parent*>
> - parent branch로부터 새 branch를 생성한다.
>
> $ git checkout **-b** <*local_branch_name*> <*remote_name*/*remote_branch_name*>
> - 원격 저장소의 branch에서 시작하는 로컬 branch를 만든다.
>
> $ git checkout **-b** <*branch*> <*tag*>
> - 태그가 가리키는 commit 기반으로 branch를 만들고, HEAD 포인터가 가리키게 한다.
>
> $ git checkout **--track** <*remote*/*branch*>
> - --track 옵션을 추가하면 로컬 저장소에 branch를 자동으로 생성한 후, remote branch를 tracking 한다.
>
> $ git checkout **--** <*filename*>
> - -- 옵션을 추가하면 수정됐지만 commit되지 않은 파일을 복구한다.

|                            | HEAD | Index | Workdir | WD Safe? |
| -------------------------- | ---- | ----- | ------- | -------- |
| **Commit Level**           |      |       |         |          |
| `reset --soft [commit]`    | REF  | NO    | NO      | YES      |
| `reset [commit]`           | REF  | YES   | NO      | YES      |
| `reset --hard [commit]`    | REF  | YES   | YES     | **NO**   |
| `checkout [commit]`        | HEAD | YES   | YES     | YES      |
| **File Level**             |      |       |         |          |
| `reset (commit) [file]`    | NO   | YES   | NO      | YES      |
| `checkout (commit) [file]` | NO   | YES   | YES     | **NO**   |