---
layout: post
title: React - Lifecycle Methods
categories: web
tags: [javascript, react]
---

# React - Lifecycle Methods

ES6 class component에서 사용 가능하고, stateless component에서는 사용할 수 없다.

Component가 instance화 될 때, 'mount process'가 다음의 순서로 시작된다.

- `constructor`
- `componentWillMount`
- `render`
- `componentDidMount`

State나 props가 변경 될 때, 'update process'가 다음의 순서로 시작된다.

- `componentWillReceiveProps`
- `shouldComponentUpdate`
- `componentWillUpdate`
- `render`
- `componentDidUpdate`

Component mount가 해제 되기 전에 다음의 순서로 시작된다.

- `componentWillUnmount`

## Methods

### `constructor(props)`

Component 초기화 시 호출된다. 초기 component 상태 및 class method를 정의한다.

### `componentWillMount()`

### `render()`

props 및 state를 읽고 element를 반환한다. component 출력을 반환하기 때문에 반드시 사용해야 한다.

### `componentDidMount()`

일반적으로 이 method에서 비동기 API를 사용한다.

### `componentWillReceiveProps(nextProps)`

nextProps와 이전 props인 this.props의 차이를 비교한다. nextProps를 component state로 사용할 수 있다.

### `shouldComponentUpdate(nextProps, nextState)`

props 또는 state가 변경되어 component가 update될 때 호출된다. 성능 최적화를 고려할 때 주로 사용된다. 문제가 되는 특정 component의 lifecycle rendering을 막을 수 있다.

### `componentWillUpdate(nextProps, nextState)`

render() method가 실행되기 전, 상태를 update할 수 있는 마지막 기회이다. render() method가 실행된 이후에는 setState() method를 사용할 수 없다.

### `componentDidUpdate(prevProps, prevState)`

DOM 조작을 하거나 추가 비동기 요청을 수행한다.

### `componentWillUnmount()`

Component 해제 전에 호출된다. Component를 초기화 한다.

### `componentDidCatch(error, info)`

React16 에서 추가된  method로 component error를 catch한다.

