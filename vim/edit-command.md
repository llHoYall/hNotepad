---
layout: post
title: Edit Command
category: vim
tags: vim
---



# Edit Command

`:edit` 명령어는 보통 다음의 동작을 한다.

- 인자로 파일 이름을 사용하면 현재 창에 해당 파일을 연다.
- 인자로 디렉토리 이름을 사용하면 해당 디렉토리에 대해 탐색기를 연다.
- 인자를 사용하지 않으면 현재 파일의 마지막 저장 버전으로 되돌린다.

`<TAB>` 키를 사용하여 파일이나 디렉토리 이름에 auto-complete 기능을 사용할 수 있다.

#### :cd command

현재 파일과 같은 디렉토리의 파일들을 편하게 작업하고 싶을 때, vim에서 다음과 같이 작업 디렉토리를 변경할 수 있다.

`:cd %:p:h`

- `%` : current file name
- `:p` :  expand to full path
- `:h` : head (last path component removed)

작업 디렉토리 자체를 변경하면 불편한 경우도 생기므로, 상황에 따라 현재 작업 중인 파일과 같은 디렉토리의 파일을 사용하는 다른 방법을 사용하자. 다음과 같은 설정을 사용하여 단축키를 사용할 수도 있다.

```vim
cnoremap %% <C-R>=fnameescape(expand('%:h')).'/'<CR>
map <leader>ew :e %%
map <leader>es :sp %%
map <leader>ev :vsp %%
map <leader>et :tabe %%
```

