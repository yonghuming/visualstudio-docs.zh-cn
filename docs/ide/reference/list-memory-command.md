---
title: "“列出内存”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory 命令"
  - "“列出内存”命令"
  - "ListMemory 命令"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# “列出内存”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

显示内存的指定范围中的内容。  
  
## 语法  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## 参数  
 `expression`  
 可选。  从此处开始显示内存的内存地址。  
  
## 开关  
 \/ANSI&#124;Unicode  
 可选。  将内存显示为对应于内存的字节的 ANSI 或 Unicode 字符。  
  
 \/Count:`number`  
 可选。  确定要显示的内存的字节数，从 `expression` 开始。  
  
 \/Format:`formattype`  
 可选。  查看**“内存”**窗口中的内存信息时使用的格式类型；可以为 OneByte、TwoBytes、FourBytes、EightBytes、Float（32 位）或 Double（64 位）。  如果使用 OneByte，则 `/Unicode` 不可用。  
  
 \/Hex&#124;Signed&#124;Unsigned  
 可选。  指定查看数字时使用的格式：有符号、无符号或十六进制。  
  
## 备注  
 不必写出完整 **Debug.ListMemory** 命令及所有开关，可以使用预定义的别名及预设给指定值的某些开关来调用此命令。  例如，不必输入：  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 可写入：  
  
```  
>df /Count:30 /Unicode  
```  
  
 下面是 **Debug.ListMemory** 命令的可用别名列表：  
  
|Alias|命令和开关|  
|-----------|-----------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory \/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## 示例  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## 请参阅  
 [“列出调用堆栈”命令](../../ide/reference/list-call-stack-command.md)   
 [“列出线程”命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)