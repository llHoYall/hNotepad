---
layout: post
title: [Plugin] Airline
category: vim
tags: vim
---

&nbsp;

# [Plugin] Airline

vim의 statusline과 tabpage를 꾸며주는 플러그인이다.

&nbsp;

테마를 선택하려면 다음 변수를 설정한다.

> :let g:airline_theme='*theme*'

Symbol을 변경하려면 다음 변수를 설정한다.

> :let g:airline_powerline_fonts=1
>
> :let g:airline_symbols_ascii=1

각 섹션을 변경하려면 'statusline' 옵션을 설정하듯이 해주면 된다.

> :let g:airline_section_b='%-0.10{getcwd()}'
>
> :let g:airline_section_c='%t'

Tabline을 표시하려면 다음 변수를 설정한다.

> :let g:airline#extensions#tabline#enabled=1

&nbsp;

## Themes

다음은 설정 가능한 테마 목록이다.

- alduin
- angr
- atomic
- aurora
- badcat
- badwolf
- base16
- base16_shell
- base16_3024
- base16_apathy
- base16_ashes
- base16_atelierdune
- base16_atelierforest
- base16_atelierheath
- base16_atelierlakeside
- base16_atelierseaside
- base16_bespin
- base16_brewer
- base16_bright
- base16_chalk
- base16_codeschool
- base16_colors
- base16_default
- base16_eighties
- base16_embers
- base16_flat
- base16_google
- base16_grayscale
- base16_greenscreen
- base16_harmonic16
- base16_hopscotch
- base16_isotope
- base16_londontube
- base16_marrakesh
- base16_mocha
- base16_monokai
- base16_ocean
- base16_oceanicnext
- base16_paraiso
- base16_pop
- base16_railscasts
- base16_seti
- base16_shapeshifter
- base16_solarized
- base16_spacemacs
- base16_summerfruit
- base16_tomorrow
- base16_twilight
- base16color
- behelit
- biogoo
- bubblegum
- cobalt2
- cool
- dark
- dark_minimal
- deus
- distinguished
- durant
- faryfloss
- hybrid
- hybridline
- jay
- jellybeans
- kalisi
- kolor
- laederon
- light
- licius
- luna
- minimalist
- molokai
- monochrome
- murmur
- onedark
- papercolor
- powerlineish
- qwq
- raven
- ravenpower
- serene
- sierra
- silver
- simple
- soda
- sol
- solarized
- term
- tomorrow
- ubaryd
- understated
- vice
- wombat
- xtermlight
- zenburn

&nbsp;

## Reference

- https://github.com/vim-airline/vim-airline