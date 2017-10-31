---
layout: post
title: Setting
category: vim
tags: vim
---

&nbsp;

# Setting

## Options

- :se[t] - 현재 설정된 옵션들의 상태를 보여준다.
- :se[t] *option* - 해당 옵션의 상태를 보여준다.
- :se[t] all - 모든 옵션들의 상태를 보여준다.
- :se[t] \[no]*option* - 해당 옵션을 enable/disable 한다.
- :se[t] *option*! - 해당 옵션의 상태를 toggle 한다.
- :se[t] *option*=*value* - 해당 옵션에 값을 지정한다.
- :setl[ocal] ... - :set과 비슷하지만, 현재 버퍼 혹은 현재 창에만 적용된다.

옵션 사이에 공백으로 구분하여 여러 옵션을 한 번에 설정할 수도 있다.

&nbsp;

## Functions

vim에는 옵션 외에도 설정할 수 있는 기능들이 있다. 옵션이 아니므로 :set 명령을 사용하지 않는다.

&nbsp;

## Setting Files

Unix, Linux, Mac 에서는 **~/.vimrc** 파일로 저장되며, Windows에서는 **~/_vimrc** 파일로 저장된다.

Syntax 파일은 **~/.vim/syntax** 폴더 안에 ***name*.vim** 파일로 저장된다.

특정 파일에만 옵션을 지정하고 싶을 때는 파일의 첫 행에 다음과 같은 방법으로 명시하면 된다.

```vim
/* vim: set ts=2 sw=2: */
```

&nbsp;

## My Options

- **se enc=utf-8**
  set encoding=utf-8
  vim 내부의 문자 인코딩을 설정한다.

- **se fenc=utf-8**
  set fileencoding=utf-8
  현재 버퍼의 문자 인코딩을 설정한다.
  - utf-8, utf8
  - ucs-bom
  - korea : 유닉스에서는 euc-kr, 윈도우즈에서는 cp949로 자동 변환.
  - euc-kr : 유닉스에서만 사용 가능
  - cp949 : 유닉스, 윈도우즈 모두 사용 가능
  - japan : 유닉스에서는 euc-jp, 윈도우즈에서는 cp932로 자동 변환.
  - latin1, ansi : ascii 형식

- **se fencs=ucs-bom,utf-8,korea**
  set fileencodings=ucs-bom,utf-8,korea
  파일의 편집을 시작할 때 고려되는 문자 인코딩 목록을 설정한다.
  ucs-bom (universal-character-set byte-order-mark) : 유니코드의 인코딩 타입을 문서 서두에 남겨서 자동으로 인코딩을 판단할 수 있도록 하기 위한 정보.

- **se ff=unix**
  set fileformat=unix
  현재 버퍼의 \<EOL> 설정을 한다.
  - dos : \<CR>\<NL>
  - unix : \<NL>
  - mac : \<CR>

- **se nocp**
  set nocompatible
  vi와 호환하지 않음.

- **syntax enable**
  현재 color scheme으로 문법 체크 기능을 사용한다.
  - syntax on : vim의 기본 설정으로 문법 체크 기능을 사용한다.
  - syntax clear : 문법 체크 기능을 사용하지 않는다. 현재 창에만 적용된다.
  - syntax off : 문법 체크 기능을 사용하지 않는다. 기능을 완전히 중지하고, 모든 버퍼에서 삭제한다.

- **se bg=dark**
  set background=dark
  배경색을 설정한다. dark와 light를 주로 사용한다.

- **colo {*scheme*}**
  colorscheme {*scheme*}
  해당 색상 테마를 사용한다. 문법 체크 기능과 연동된다.

- **filet plugin indent on**
  filetype plugin indent on
  - filet on : file type을 자동으로 인식하게 한다. $VIMRUNTIME/filetype.vim 파일에 정의되어 있다.
  - filet plugin on : file type을 인식해 plugin 파일을 loading하게 한다.
  - filet indent on : file type을 인식해 indent 파일을 loading하게 한다.

- **se ai**
  set autoindent
  자동 들여쓰기. 이전 라인의 들여쓰기 만큼 들여쓴다.

- **se bs=indent,eol,start**
  set backspace=indent,eol,start
  \<BS> 키의 동작을 설정한다.
  - indent : allow backspacing over autoindent
  - eol : allow backspacing over line breaks
  - start : allow backspacing over the start of insert;

- **se cb=unnamed**
  set clipboard=unnamed
  모든 복사, 삭제, 변경 시 * 레지스터를 사용한다. 즉, 시스템 클립보드를 사용한다.

- **se cc=80**
  set colorcolumn=80
  print margin 표시.

- **se cin**
  set cindent
  c 스타일 들여쓰기. 블록 시작 및 종료 시 들여쓰기를 맞춰준다. ({, } 기호 등)

- **se noet**
  set noexpandtab
  tab대신 space로 변경하지 않는다.

- **se fdm=marker**
  set foldmethod=marker
  Fold 방법을 설정한다.
  - marker : {{{, }}} 기호를 주석과 함께 사용하여 마킹할 수 있다.

- **se hls**
  set hlsearch
  검색 시 하이라이팅을 해준다.

- **se ic**
  set ignorecase
  검색 시 대소문자를 무시한다.

- **se is**
  set incsearch
  검색 패턴입력을 할때마다 해당 패턴을 찾아 이동시켜준다.

- **se lcs=tab:▸\ ,eol:¬**
  set listchars=tab:▸\ ,eol:¬
  :list 명령어 사용 시 표시될 문자를 설정하며, comma로 다중 설정이 가능하다.

- **se ls=2**
  set laststatus=2
  상태창 표시 여부를 설정한다.
  - 0 : 표시하지 않는다.
  - 1 : 2개 이상의 창이 열려있을 때만 표시한다.
  - 2 : 항상 표시한다.

- **se nu**
  set number
  라인 번호 표시.

- **se rtp+={*path*}**

  set runtimepath+={*path*}

- **se ru**
  set ruler
  현재 커서 위치를 표시해준다.

- **se scs**
  set smartcase
  ignorecase가 활성화 상태일때만 동작한다. 검색 패턴에 대소문자가 섞여있을 경우, 대소문자를 무시하지 않는다.

- **se si**
  set smartindent
  좀 더 편하게 indent를 해준다.

- **se sm**
  set showmatch
  매칭되는 괄호를 표시해준다.

- **se stl=%n%#cursorcolumn#\ %m%r%F%=%P%%\ %l:%v\ %y\\[%{&fileformat}\\]\\[%{&fileencoding}\\]**
  set statusline=...
  상태바를 표시한다.
  %이후 원하는 아이템을 명시한다.

  {} 혹은 !를 붙이면 아이템은 evaluation 한다.

  공백문자 등은 escape를 붙인다.

  - l : Line number
  - v : Virtual column number.
  - P : Percentage through file of displayed window.
  - = : Separation point between left and right aligned items.
  - a : Argument list status as in default title.
  - h : Help buffer flag, text is "[help]".
  - m : Modified flag, text is "[+]".
  - r : Readonly flag, test is "[RO]".
  - F : Full path to the file in the buffer.
  - y : Type of file in the buffer.

- **se  sts=2**
  set softtabstop=2
  \<TAB>, \<BS> 키를 누를 때, 적용되는 공백의 갯수.

- **se sua+=.py**
  set suffixesadd+=.py
  gf 명령으로 파일을 찾을 때, 참고하는 파일 목록을 설정한다. comma로 이어서 사용한다.

- **se sw=2**
  set shiftwidth=2
  블록 단위 간격. 즉 cindent에 영향을 준다.

- **setf {*filetype*}**
  setfiletype {*filetype*}

- **se ts=2**
  set tabstop=2
  tab을 눌렀을 때의 간격.

- **se tw=0**
  set textwidth=0
  화면의 너비. 이 값보다 긴 문장은 자동 개행된다. 0이면 disable.

- **se vb**
  set visualbell
  비프음 대신에 화면을 깜빡인다.

- **se nowrap**
  화면보다 긴 문장을 자동 개행하지 않는다.
