---
layout: post
title: Powershell Posh-Git
category: shell
tags: [shell, powershell, module]
---

&nbsp;

# Powershell Posh-Git

Powershell에서 git을 좀 더 쉽게 사용하게 해주는 모듈이다.

&nbsp;

### Installation

>  Install-Module -Name posh-git

&nbsp;

### Using

> Import-Module -Name posh-git

&nbsp;

### Setting

Command-Line에서 다음 명령을 사용하여 prompt를 꾸밀 수 있다.

- $GitPromptSettings.DefaultPromptPrefix = '[\$(hostname)]'
- $GitPromptSettings.DefaultPromptSuffix = ' > '
- $GitPromptSettings.DefaultPromptAbbreviateHomeDirectory = \$true




다른 방법으로, $profile 스크립트에 다음과 같이 스크립트 함수를 만드는 방법으로 꾸밀 수도 있다.

```powershell
14 function prompt {
 15   $origLastExitCode = $LASTEXITCODE
 16
 17   $curPath = $ExecutionContext.SessionState.Path.CurrentLocation.Path
 18   if ($curPath.ToLower().StartsWith($Home.ToLower())) {
 19     $curPath = "~" + $curPath.SubString($Home.Length)
 20   }
 21
 22   Write-Host -NoNewline -ForegroundColor Green "[$(hostname)] "
 23   Write-Host -ForegroundColor Blue $curPath
 24   Write-VcsStatus
 25   $LASTEXITCODE = $origLastExitCode
 26   "$('>' * ($nestedPromptLevel + 1)) "
 27 }
 28
 29 Import-Module posh-git
 30 $global:GitPromptSettings.BeforeText = '['
 31 $global:GitPromptSettings.AfterText  = '] '
```

