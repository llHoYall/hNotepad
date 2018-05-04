---
layout: post
title: Heroku - Distribution
categories: web
tags: [heroku]
---

# Heroku - Distribution

Heroku를 사용하여 application을 배포할 수 있다.

먼저 다음의 사이트에서 계정을 만든다.

>  https://www.heroku.com/

## Installation

- MAC

> $ brew install heroku-toolbelt

## create-react-app

create-react-app으로 만든 application을 heroku로 배포해보자.

> $ git init
>
> $ heroku create -b https://github.com/<account>/<project>
>
> $ git add .
>
> $ git commit -m "react-create-app on Heroku"
>
> $ git push heroku master
>
> $ heroku open

