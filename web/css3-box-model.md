---
layout: post
title: CSS3 - Box Model
categories: [web, css3]
tags: css3
---

# CSS3 - Box Model

```css
+----------------------+
|       Margin         |
| +------------------+ |
| |     Border       | |
| | +--------------+ | |
| | |   Padding    | | |
| | | +----------+ | | |
| | | | Contents | | | |
| | | +----------+ | | |
| | +--------------+ | |
| +------------------+ |
+----------------------+
```

## Margin and Padding

```css
/* 개별 스타일링 */
margin-top, margin-right, margin-bottom, margin-left
padding-top, padding-right, padding-bottom, padding-left

/* 축약 스타일링 */
margin: <top> <right> <bottom> <left>
margin: <top> <left-right> <bottom>
margin: <top-bottom> <left-right>
margin: <top-right-bottom-left>
```

연달아 있는 element의 경우 margin 속성이 맞닿게 되면 작은 값을 가지는 쪽의 margin은 무시되어 병합되는 현상이 발생한다.

margin과 padding은 px 단위로 지정을 하며, 음수도 가능하다.

## Absolute, Relative, Fixed

HTML element를 배치하는 방법은 크게 3가지가 있다.

```css
selector {
    position: absolute | relative | fixed;
}
```

### Absolute

자신의 부모를 기준으로 상대적인 위치를 설정하는 방법이다.

### Relative

원래 있어야할 위치를 기준으로 상대적인 위치를 설정하는 방법이다.

### Fixed

화면을 출력하고 있는 브라우저 화면을 기준으로 위치를 설정하는 방법이다.

## z-index Attribute

```css
selector {
    z-index: <integer>;
}
```

Rendering 시 쌓이는 순서를 정한다. 숫자가 클수록 위쪽에 놓이며, 음수도 가능하다. 같은 값이라면 HTML 코드 상에서 뒤에 있는 element가 위로 놓인다.

기본 값은 `auto`이며 쌓이는 순서가 부모 element와 동일함을 나타낸다.

`position` 속성이 `static`이면 의미가 없다.

## float Attribute

다른 element들을 고려하여 상호 위치를 결정할 때 사용된다.

```css
selector {
    float: left | right | none | inherit;
}
```

## clear Attribute

float 속성을 제거한다.

```css
selector {
    clear: none | left | right | both;
}
```

