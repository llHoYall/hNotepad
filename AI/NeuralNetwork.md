---
layout: post
title: Neural Network
category: AI
tags: [AI, NeuralNetwork]
---

&nbsp;

# Neural Network

신경망에서는 학습 데이터에서 모델(신경망)을 찾아내는 기법을 학습 규칙이라고 부른다.

~~~mermaid
graph LR
	D[학습 데이터] -.-> E(학습규칙)
  E -.-> B
	A[입력 데이터] --> B[신경망]
	B --> C[결과]
~~~

신경망의 노드는 다음과 같다.

~~~mermaid
graph LR
	b --> v(v)
	x1 -->|w1|v
	x2 -->|w2|v
	x3 -->|w3|v
	v --> y
~~~

신경망의 노드는 다음과 같은 과정을 거쳐 신호를 출력한다.

1. 입력 신호의 가중합을 구한다.

$$
v = w1*x1 + w2*x2 +w3*x3 + b
$$

$$
v = \sum^N wx + b
$$

2. 활성함수에 가중합을 입력해 얻은 값을 외부로 출력한다.

$$
y = \varphi(v) = \varphi(wx + b)
$$

위와 같이 입력층-출력층으로만 구성된 신경망을 **단층 신경망**이라고 한다.

입력층-은닉층-출력층으로 구성된 신경망을 **다층 신경망**이라고 한다.

다층 신경망 중 은닉층이 2개 이상인 다층 신경망을 **심층 신경망**이라고 한다.

이와 대비해 은닉층이 1개인 다층 신경망을 **얕은(shallow, vanilla) 신경망**이라고 한다.



선형함수를 은닉노드들의 활성함수로 사용하면 은닉층을 추가한 효과가 없어지기 때문에 수학적으로 은닉층이 없는 단층 신경망과 똑같아 진다. 은닉층이 아닌 출력 노드의 활성함수로 사용하는 것은 괜찮다.

회귀 문제에서는 출력 노드들의 활성함수로 선형함수를 쓰기도 한다.

