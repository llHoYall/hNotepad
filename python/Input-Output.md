---
layout: post
title: Input/Output
category: python
tags: python
---

&nbsp;

# Input/Output

### Output

다음과 같이 formatter를 사용할 수 있다.

```python
for n in [2, 3, 4, 5, 6, 7, 8, 9]:
    print("-- Table {0} --".format(n))
    for i in [1, 2, 3, 4, 5, 6, 7, 8, 9]:
        print("{0} * {1} = {2}".format(n, i, n * i))
```

