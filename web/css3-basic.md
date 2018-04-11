---
layout: post
title: CSS3 - Basic
categories: [web, css3]
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

