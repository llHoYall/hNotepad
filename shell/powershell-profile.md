---
layout: post
title: Powershell Profile
category: shell
tags: [shell, powershell]
---

&nbsp;

# Powershell Profile

powershell에서도 bash와 같이 프로파일을 설정할 수 있지만, 기본은 없으므로 만들어 줘야 한다.

먼저 권한 확인을 한다.

> $ Get-ExecutionPolicy

적절한 권한이 설정되어 있지 않다면 설정해준다. AllSigned나 Unrestricted도 가능하지만 RemoteSigned로도 충분하다.

> $ Set-ExecutionPolicy RemoteSigned

profile을 만들어 준다.

> $ New-Item -Path \$profile -ItemType file -Force

profile을 편집한다.

> $ notepad \$profile



다음과 같이 설정을 할 수 있다.

```powershell
Set-Alias	vim	"C:\Program Files (x86)\vim\vim80\vim.exe"

Function Edit-Profile {
  vim $profile
}

Function Edit-Vimrc {
  vim $HOME\_vimrc
}
```

