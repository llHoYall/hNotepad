---
layout: post
title: CSS3 - Basic
categories: [web, css3]
tags: [web, css3]
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

##### selector

- \* : all.
- tag : tag selector, type selector.
- \# : id selector.
- . : class selector.

