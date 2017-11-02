---
layout: post
title: Powershell PSColor
category: shell
tags: [shell, powershell, module]
---

&nbsp;

# Powershell PSColor

Powershell에서 각종 정보에 색상을 입혀준다.

&nbsp;

### Installation

> Install-Module -Name PSColor

&nbsp;

### Using

> Import-Module -Name PSColor

&nbsp;

### Setting

기본 color 설정은 다음과 같이 되어 있다.

```powershell
$global:PSColor = @{
    File = @{
        Default    = @{ Color = 'White' }
        Directory  = @{ Color = 'Cyan'}
        Hidden     = @{ Color = 'DarkGray'; Pattern = '^\.' } 
        Code       = @{ Color = 'Magenta'; Pattern = '\.(java|c|cpp|cs|js|css|html)$' }
        Executable = @{ Color = 'Red'; Pattern = '\.(exe|bat|cmd|py|pl|ps1|psm1|vbs|rb|reg)$' }
        Text       = @{ Color = 'Yellow'; Pattern = '\.(txt|cfg|conf|ini|csv|log|config|xml|yml|md|markdown)$' }
        Compressed = @{ Color = 'Green'; Pattern = '\.(zip|tar|gz|rar|jar|war)$' }
    }
    Service = @{
        Default = @{ Color = 'White' }
        Running = @{ Color = 'DarkGreen' }
        Stopped = @{ Color = 'DarkRed' }     
    }
    Match = @{
        Default    = @{ Color = 'White' }
        Path       = @{ Color = 'Cyan'}
        LineNumber = @{ Color = 'Yellow' }
        Line       = @{ Color = 'White' }
    }
	NoMatch = @{
        Default    = @{ Color = 'White' }
        Path       = @{ Color = 'Cyan'}
        LineNumber = @{ Color = 'Yellow' }
        Line       = @{ Color = 'White' }
    }
}
```

원하는 색상으로 변경을 하고 싶으면 prompt에서 다음과 같은 명령을 사용한다.

> $global:PSColor.File.Executable.Color = 'Blue'

