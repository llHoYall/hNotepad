---
layout: post
title: JavaScript - Closure
categories: web
tags: javascript
---

# JavaScript - Closure

클로저는 자신의 범위 밖에 있는 변수들에 접근할 수 있는 함수를 의미한다.

```javascript
function f() {
    var b = "b";
    return function() {
        return b;
    }
}

var n = f();
n();
//>>> "b"
```

전역  함수 n은 함수 f의 범위를 공유한다.

```javascript
var n;
function f() {
	var b = "b";
    n = function() {
        return b;
    }
}

f();
n();
//>>> "b"
```

함수 f를 실행하면 전역 변수 n에 함수 f의 범위가 공유된다.

```javascript
function f(arg) {
    var n = function() {
        return arg;
    }
    arg++;
    return n;
}

var m = f(123);
m();
//>>> 124
```

함수 n은 함수 f의 범위내에 있는 것을 참조하고 있기 때문에 함수 f의 모든 처리가 끝난 후에 처리된다.

```javascript
function f() {
    var a = [];
    var i;
    for (i = 0; i < 3; i++) {
        a[i] = function() {
            return i;
        }
    }
    return a;    
}
var b = f();
b[0]();
//>>> 3
b[1]();
//>>> 3
b[2]();
//>>> 3
```

위의 예와 마찬가지로 함수 f의 처리가 다 끝난 후에 실제 참조가 이루어진다.

