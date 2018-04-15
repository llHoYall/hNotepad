---
layout: post
title: CSS3 - Basic
categories: web
tags: css3
---

# CSS3 - Basic

####  Applying

```css
/* Inline */
<div style="color: red;"></div>

/* Embedded (Internal Style Sheet) */
<head>
	<style type="text/css">
	<!--
		body {
    		font-size: 14pt;
		}
	//-->
	</style>
</head>

/* External File Link (External Style Sheet) */
<head>
	<link rel="stylesheet" type="text/css" href="stylesheet.css">
</head>
```

#### Comments

```css
/* Comments */
```

#### Grammar

```css
selector[, selector] {
    property: value;
    [property: value;]
}
```

##### Selector

- `*` : Universal selector.
- `element` : Element selector, Tag selector, Type selector.
- `.` : Class selector.
- `#` : ID selector.


##### Combinators

- `selector selector` : Descendant combinator.
- `selector > selector` : Child combinator.
- `selector + selector` : Adjacent sibling combinator.


##### Pseudo-classes

- `element :first-child`
- `element :lang(<language-code>)`
- `element :link`
- `element :visited`
- `element :active` : 마우스를 누르고 있는 상태.
- `element :hover`
- `element :focus`

##### Pseudo-elements

- `element :first-line`
- `element :first-letter`
- `element :before`
- `element :after`

##### At-Rules

- `@import url('path')` : 외부 CSS를 불러온다.

##### !important Rule

해당 스타일을 항상 적용되도록 한다. 특정 페이지 내에서 부트스트랩 같은 외부 라이브러리의 스타일을 덮어쓸 뎡우에만 사용하도록 하자. 플러그 인이나 사이트 전체에 적용되는 CSS에는 사용하지 말라.

```css
!important selector {
    property: value;
}

selector {
    property: value !important;
}
```

##### Length

많은 CSS3 속성들은 length를 값으로 갖는다.  Length는 다음과 같은 값을 가질 수 있다.

- `em` : Relative to the font-size of the element.
- `ex` : Relative to the x-height of the current font.
- `ch` : Relative to witdh of the "0".
- `rem` : Relative to font-size of the root element.
- `vw` : Relative to 1% of the width of the viewport.
- `vh` : Relative to 1% of the height of the viewport.
- `vmin` : Relative to 1% of viewport's smaller dimension.
- `vmax` : Relative to 1% of viewport's larger dimension.
- `%`


##### Color

CSS3에서 색깔을 나타내는 방법은 여러 가지가 있다.

- Hexadecimal Color : `#RRGGBB`
- RGB Color : `rgb(R, G, B)`
- RGBA Color : `rgba(R, G, B, Opacity)`
- HSL Color : `hsl(h, s, l)`
- HSLA Color : `hsla(h, s, l, alpha)`
- Predefined Color : `name`

```css
background-color: #113355;
background-color: rgb(127, 24, 36);
background-color: rgba(231, 34, 157, 0.5);
background-color: hsl(180, 70%, 50%);
background-color: hsla(120, 60%, 70%, 0.3);
background-color: red;
```

