---
layout: post
title: HTML5 - Basic
categories: web
tags: html5
---



# HTML5 - Basic

#### DTD (Document Type Definition)

```html
<!doctype html>
```

#### Comments

```html
<!-- Comments -->
```

#### Elements

```html
<tag attribute="value">contents</tag>
```

##### Attributes

- id: 문서 전체에서 고유한 값을 부여한다.
- class: 유사한 요소를 분류한다.

#### Tags

- html, head, title, body
- p, br
- a, img, input
- div, span

#### DOM (Document Object Model)

##### Properties

- (Element).innerHTML: 텍스트 값.

- (Element).nodeName: 노드의 이름.

- (Element).nodeValue: 노드의 값.

- (Element).parentNode: 노드의 부모 노드.

- (Element).childNodes: 노드의 자식 노드.

- (Element).attributes: 속성.

##### Methods

- (Element).appendChild(node): 새로운 노드를 추가한다.
- (Element).removeChild(node): 해당 노드를 제거한다.
- (Element).getElementById(id): 자식 노드 중 해당 id 값을 갖는 노드를 찾는다.
- (Element).getElementsByTagName(name): 자식 노드 중에서 해당 tag 이름을 갖는 노드를 찾는다.

