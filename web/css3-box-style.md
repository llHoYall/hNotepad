---
layout: post
title: CSS3 - Box Style
categories: web
tags: css3
---

# CSS3 - Box Style

박스 스타일에 관한 속성들이다.

- `border`

  - `border-style border-width border-color`

  ```css
  border: solid 1px red;
  ```

- `border-style`

  - `none | hidden | dotted | dashed | solid | double | groove | ridge | inset | outset | initial | inherit`

  ```css
  border-style: dashed;
  ```

- `border-width`

  - `medium | thin | thick | length | initial | inherit`

  ```css
  border-width: 10px;
  ```

- `border-color`

  - `color | transparent | initial | inherit`

  ```css
  border-color: blue;
  ```

- `border-radius`

  - length를 하나만 입력하면 둥근 모서리를 만든다.
  - 반지름 너비 / 반지름 높이로 타원형 표현이 가능하다.
  - `length / length | initial | inherit`

- `border-image`

  - `source slice width outset repeat | initial | inherit`

  ```css
  border-image: url(border.png) 30 30 round;
  /* webkit 계열 */
  -webkit-border-image: url(border.png) 50 round;
  /* mozilla 계열 */
  -moz-border-image: url(border.png) 20% round;
  /* opera 계열 */
  -o-border-image: url(border.png) 50 60 round;
  ```

- `transform`

  - `none | transform-functions | initial | inherit`

  ```css
  transform: translate(130px, 120px);
  /* webkit 계열 */
  -webkit-transform: rotate(45deg);
  /* mozilla 계열 */
  -moz-transform: scale(1.5);
  /* opera 계열 */
  -o-transform: skew(90deg);
  /* ms 계열 */
  -ms-transform: rotate(60deg);
  ```

- `box-shadow`

  - 기본 값은 none이다.
  - h-offset, v-offset은 필수 값이다.
  - blur는 선택 값이다.
  - spread는 선택 값이다. 음수도 가능하다.
  - color는 선택 값이다.
  - inset은 선택 값이다.
  - `none | h-offset v-offset blur spread color inset | initial | inherit`

  ```css
  box-shadow: 50px 50px 10px 20px blue;
  box-shadow: 50px 50px 10px 20px pink inset;
  ```

- `background-clip` : 배경 이미지의 출력 영역을 설정한다.

  - `border-box | padding-box | content-box | initial | inherit`

  ```css
  background-clip: padding-box;
  ```

  ​

- `background-origin` : 배경 이미지의 기준 위치를 조정하는 방법을 결정한다.

  - `padding-box | border-box | content-box | initial | inherit`

  ```css
  background-origin: content-box;
  ```

- `background-image`

  - 여러 개의 배경 이미지를 입력할 수 있다. 각각의 속성 값도 순서대로 입력하면 된다.
  - image에는 url('URL'), linear-gradient(), radial-gradient(), repeating-linear-gradient(), repeating-radial-gradient()가 올 수 있다.
  - `image | none | initial | inherit`

  ```css
  /* Multiple Backgrounds */
  selector {
      background-images: url("img1.jpg"), url("img2.jpg");
      background-repeat: repeat-x;
      background-position: top center, bottom center;
  }
  /* Gradient */
  background-image: linear-gradient(red, yellow);
  /* Gradient - webkit 계열 */
  background-image: -webkit-linear-gradient(left, black, white);
  /* Gradient - mozilla 계열 */
  background-image: -moz-linear-gradient(left, black, white);
  /* Gradient - MS 계열 */
  background-image: -ms-linear-gradient(left, black, white);
  /* Gradient - opera 계열 */
  background-image: -o-linear-gradient(left, black, white);
  ```

  ​


