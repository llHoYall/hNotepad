---
layout: post
title: CSS3 - Text Style
categories: web
tags: css3
---

# CSS3 - Text Style

텍스트 스타일에 관한 속성들이다.

- `font-size`

  - 기본 값은 medium.

  - `xx-small | x-small | small | medium | large | x-large | xx-large | smaller | larger | length | initial | inherit`

  ```css
  font-size: 30px;
  ```

- `font-family` : 시스템 폰트 중에서 어떤 폰트를 사용할 것인지 지정한다.

  - 먼저 정의된 폰트가 우선권을 가진다.
  - `family-name | generic-family | initial | inherit`

  ```css
  font-family: Arial, Sans-serif;
  ```

- `font-weight`

  - 400은 기본 값인 normal이고, 700은 bold이다.
  - `normal | bold | bolder | lighter | number | initial | inherit`

  ```css
  font-weight: bold;
  ```

- `text-shadow`

  - 기본 값은 none이다. 
  - h, v는 필수이며, 음수도 가능하다. 
  - blur는 선택이며 기본 값은 0이다. 
  - color는 선택이다.
  - `h-shadow` `v-shadow` `[blur-radius]` `[color | none | initial | inherit]`

  ```css
  text-shadow: 10px 10px 4px #222;
  ```

- `-webkit-text-stroke` : 텍스트에 외곽선 효과를 준다.

  - `length(px, cm, ...)` `color`
  - webkit 외의 브라우저들은 text-shadow를 4방향으로 주어서 흉내낼 수 있다.

  ```css
  -webkit-text-stroke: 2px #222;
  /*
  text-shadow: 
  	-1px -1px 0 #222,
  	1px -1px 0 #222,
  	-1px 1px 0 #222,
  	1px 1px 0 #222;
  */
  ```

- `::selection` : Selector이며, 텍스트 등을 드래그할 때 배경색을 변경한다.

  ```css
  selector::selection {}
  /* mozilla 계열 */
  selector::-moz-selection {}
  ```

- `text-transform` : 대소문자를 변경한다.

  - `none | capitalize | uppcase | lowercase | initial | inherit`

  ```css
  text-transform: capitalize;
  ```

- `transform`

  - `none | transform-functions | initial | inherit`

  ```css
  transform: rotate(30deg);
  /* webkit 계열 */
  -webkit-transform: skewY(45deg);
  /* mozilla 계열 */
  -moz-transform: scaleY(1.5);
  ```

- `@font-face` : 서버에 있는 폰트를 지정한다.

  - .ttf(true type font) 형태도 사용 가능하지만, 용량이 크기 때문에 웹 폰트 전용인 .eot, .woff (web open font format), .otf (open type font), svg (scalable vector graphics) 형태의 폰트를 지원한다.
  - .eot는 IE 에서만 지원한다.
  - .woff는 IE9 이상과 chrome, FF 모두 지원한다.
  - font-weight를 지정하면 폰트에 내장된 'bold font'를 적용한다.

  ```css
  @font-face {
      font-family: 'LeagueGothic';
      src: url('../font/League_Gothic.eot');
      src: url('../font/League_Gothic.eot?#iefix') format('eot'),
          url('../font/League_Gothic.woff') format('woff'),
          url('../font/League_Gothic.ttf') format('ttf'),
          url('../font/League_Gothic.svg#webfontFHzvtkso') format('svg');
      font-weight: bold;
      font-style: normal;
  }
  ```

  ```css
  @font-face {
      font-family: 'CoolFont';
      font-style: normal;
      src: url('../font/CoolFontStd.ttf')
  }
  @font-face {
      font-family: 'CoolFont';
      font-style: italic;
      src: url('../font/CoolFontItalic.ttf')
  }
  .whichFont {
      font-family: 'CoolFont';
  }
  ```

- `unicode-range`

  - 생략 시 폰트 파일 내에 포함된 전체 문자를 사용한다.

  ```css
  unicode-range: U+000-49f, U+2000-27FF, U+2900-2BFF, U+1D400-1D7FF
  ```

- `word-wrap`

  - `normal | break-word | initial | inherit`

  ```css
  word-wrap: break-word;
  ```

## Reference

- http://www.google.com/fonts