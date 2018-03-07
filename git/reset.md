---
layout: post
title: Reset
category: git
tags: git
---



# Reset

Commit을 해제하는 명령어이다.

> $ git reset <*commit*>
> - Commit을 해제한다.
>  즉, INDEX를 현재 HEAD가 가리키는 스냅샷으로 업데이트 한다.
>  Ex) $ git reset HEAD^
>
> $ git reset <*file*>
> - HEAD에서 file을 Index로 옮긴다.
>    $ git reset --mixed HEAD \<file>과 같다.
>
> $ git reset HEAD <*filename*>
> - Staging area의 파일을 staging area에서 삭제해 파일의 수정사항이 다음commit에 저장되지 않도록 한다.
>
> $ git reset <*commit*> <*file*>
> - Commit에서 Index로 파일을 옮긴다.
>
> $ git reset **--soft** <*commit*>
> - --soft 옵션을 추가하면 HEAD가 가리키는 commit만 바꾼다.
>   Ex) $ git reset --soft HEAD~
>
> $ git reset **--hard** <*commit*>
> - --hard 옵션을 추가하면 working directory까지 업데이트 한다.
>   Ex) $ git reset --hard HEAD~
>
> $ git reset **--merge** *ORIG_HEAD*
> - --merge 옵션을 추가하면 최신 merge를 통해 적용된 모든 commit을 현재 branch에서 삭제한다.

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

