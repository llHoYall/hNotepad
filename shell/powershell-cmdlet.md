---
layout: post
title: Powershell Cmdlet
category: shell
tags: [shell, powershell]
---

&nbsp;

# Powershell Cmdlet

- **Get-Help**

- **Copy-Item** {*from*} {*to*} : cpi, cp, copy
  -Recurse

- **Get-ChildItem** {*path*} : gci, ls, dir
  -Exclude
  -Recurse
  -Force
  -Directory
  -File
  -Hidden
  -ReadOnly
  -System

- **Invoke-WebRequest** : iwr, wget, curl
  - -Uri {*uri*}
  - -OutFile {*string*}

- **Invoke-Expression** {*script file*} : iex

- **New-Item** {path} : ni
  -Type {directory|file}
  -Force
  -Value "*data*"

- **Remove-Item** {*path*} : ri, rd, erase, rm, rmdir, del
  -Recurse
  -Force
  -Include {*file*}
  -Exclude {*file*}

- **Rename-Item** {*current*} {*new*} : rni, ren

- **Set-Alias** {*name*} {*path*}

- **Set-Location** {*path*} : sl, cd, pwd, chdir

- **Test-Path** {*path*}
  return True|False


