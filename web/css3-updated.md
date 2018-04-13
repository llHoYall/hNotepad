---
layout: post
title: CSS3 - Updated
categories: [web, css3]
tags: css3
---

# CSS3 - Updated

CSS3에서 추가된 내용이다.

## Borders

- `border-radius`
- `box-shadow`
- `border-image`

## Backgrounds

- `background-size`
- `background-origin` : 배경 이미지의 위치를 어디부터 시작할지 지정한다.
  - `padding-box | border-box | content-box | initial | inherit` 

## Text Effects

- `text-overflow`
- `text-align-last`
- `text-shadow`
- `word-break`
- `word-wrap`

## Fonts

- `@font-face` : 글꼴이 없는 경우 웹 서버를 통하여 다운받아 사용할 수 있게 해준다.
- `font-stretch` : 글꼴의 장평을 결정한다.
- `unicode-range` : 글꼴이 지원하는 유니코드의 범위를 지정해준다.

## 2D Transforms

- `transform`
  - `translate()`, `rotate()`, `scale()`, `skew()`, `matrix()`

## 3D Transforms

- `transform`
  - `rotateX()`, `rotate()`

## Transitions

- `transition`
- `transition-property` : 어떤 속성에 transition 효과를 줄 지 지정한다.
- `transition-duration`
- `transition-timing-function` : 각 구간별로 진행 속도를 다르게 할 수 있는 시간에 대한 함수를 지정한다.
- `transition-delay`

## Animations

- `@Keyframes` : 애니메이션의 기본 단위를 생성한다.
- `animation` : 키 프레임을 연결하여 애니메이션이 진행되도록 한다.

## Multiple Columns

- `column-count`
- `column-gap`
- `column-rule` : column 사이의 경계선에 속성을 지정한다.
- `column-rule-color`
- `column-rule-style`
- `column-rule-width`
- `column-span`
- `column-width`
- `columns`

## User Interface

- `appearance`
- `box-sizing`
- `outline`
- `resize`