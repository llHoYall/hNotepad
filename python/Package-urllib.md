---
layout: post
title: Package - urllib
category: python
tags: python
---

&nbsp;

# Package - urllib

URL 관련 패키지이다.

```python
from urllib.parse import urlparse
url = "https://www.google.co.kr/search?q=python+urllib&oq=python+urllib&aqs=chrome..69i57j0l5.6461j0j7&sourceid=chrome&ie=UTF-8"
ups = urlparse(url)
print(ups)
```

