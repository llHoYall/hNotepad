---
layout: post
title: CSS3 - Flexible Box
categories: web
tags: css3
---

# CSS3 - Flexible Box

가변적인 박스를 쉽게 만들게 해주는 기술이다.

## 기본 개념

- Flexible Box = Parent Box
  부모 박스에 `display: flex;` 속성을 준다.
- Child Box = Flex Item
- 가로, 세로 방향에 대해 주축과, 교차축이 있고, 축의 방향과 시작과 끝을 정할 수 있다.

## 속성

### `display`
  - `flex` : 블록 수준의 플렉서블 박스.
  - `inline-flex` : 인라인 수준의 플렉서블 박스.

### `flex-direction`

- `row` : 박스를 왼쪽에서 오른쪽으로 배치한다.
- `row-reverse` : 박스를 오른쪽에서 왼쪽으로 배치한다.
- `column` : 박스를 위에서 아래로 배치한다.
- `column-reverse` : 박스를 아래에서 위로 배치한다.

### `flex-wrap`

- `nowrap` : 박스의 크기를 줄여서라도 한 줄로 배치한다. (기본값)
- `wrap` : 박스의 크기를 줄이지 않고 여러 줄로 배치한다.
- `wrap-reverse` : wrap 속성과 같으나 역방향으로 배치한다.

### `flex-flow`

- flex-direction flex-wrap : 2가지 속성을 동시에 지정한다.

### `justify-content`

- `flex-start` : 박스를 주축의 시작 지점으로 배치한다. (기본값)
- `flex-end` : 박스를 주축의 끝 지점으로 배치한다.
- `center` : 박스를 중앙으로 배치한다.
- `space-between` : 박스를 양끝으로 붙이고 박스 사이를 동일한 간격으로 배치한다.
- `space-around` : 박스의 양 끝을 동일한 간격으로 띄워서 배치한다.

### `align-items`

- `stretch` : 박스를 교차축 방향으로 확장하여 배치한다. (기본값)
- `flex-start` : 박스를 교차축의 시작 지점에 배치한다.
- `flex-end` : 박스를 교차축의 끝 지점에 배치한다.
- `center` : 박스를 교차축의 중앙에 배치한다.
- `baseline` : 박스들을 박스의 글자 베이스라인에 맞춰 배치한다. 

### `align-self`

- `auto` : 부모의 align-items 속성을 상속받는다.

### `align-content`

- `stretch`, `flex-start`, `flex-end`, `center`, `space-between`, `space-around` : 박스가 여러줄 일 떄만 적용된다.

### `order`

- 입력된 정수 값에따라 박스가 배치된다.

### `flex`

- flex-grow flex-shrink flex-basis
  - 0 1 auto (기본값)
  - 0 auto (0 1 auto와 같다)
  - initial (0 1 auto와 같다)
  - auto (1 1 auto와 같다)
  - none (0 0 auto와 같다)
- `flex-grow` : 플렉서블 박스에 여백이 있을 때 아이템의 크기를 늘린다.
- `flex-shrink` : 플렉서블 박스안의 플렉스 아이템의 크기가 넘칠 경우 크기를 줄일 수 있다.
- `flex-basis` : 플렉스 아이템의 기본 크기를 설정한다.

