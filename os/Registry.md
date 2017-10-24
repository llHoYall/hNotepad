---
layout: post
title: Registry
category: vim
tags: vim
---

&nbsp;

# Registry

.reg 파일은 다음과 같이 만든다.

먼저 파일의 헤더에 다음 내용을 넣는다.

```powershell
Windows Registry Editor Version 5.00
```



다음으로 편집할 카테고리를 대괄호로 만든다. 예를 들면, 다음과 같다.

```powershell
[HKEY_CURRENT_USER\Console]
```

이제 이 아래에 **키=값** 형식으로 편집을 한다. 예를 들면, 다음과 같다.

```powershell
"ColorTable00"=dword:00000000
```



특정 카테고리 전체를 삭제하려면 다음의 예와 같이 카테고리명 앞에 -를 붙여준다.

```powershell
[-HKEY_CURRENT_USER\Console]
```

특정 키만 삭제하려면 다음의 예와 같이 해당 키의 값에 -를 붙여준다.

```powershell
"ColorTable00"=-
```

특정 키의 값만 삭제하려면 다음과 같이 값 부분을 비워준다.

```powershell
"ColorTable00"=""
```

