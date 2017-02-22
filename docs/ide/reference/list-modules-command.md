---
title: "“列出模块”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules 命令"
  - "“列出模块”命令"
  - "ListModules 命令"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “列出模块”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

列出当前进程的模块。  
  
## 语法  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### 参数  
 \/Address:`yes|no`  
 可选。  指定是否显示模块的内存地址。  默认值为 `yes`。  
  
 \/Name:`yes|no`  
 可选。  指定是否显示模块的名称。  默认值为 `yes`。  
  
 \/Order:`yes|no`  
 可选。  指定是否显示模块的顺序。  默认值为 `no`。  
  
 \/Path:`yes|no`  
 可选。  指定是否显示模块的路径。  默认值为 `yes`。  
  
 \/Process:`yes|no`  
 可选。  指定是否显示模块的进程。  默认值为 `no`。  
  
 \/SymbolFile:`yes|no`  
 可选。  指定是否显示模块的符号文件。  默认值为 `no`。  
  
 \/SymbolStatus:`yes|no`  
 可选。  指定是否显示模块的符号状态。  默认值为 `yes`。  
  
 \/Timestamp:`yes|no`  
 可选。  指定是否显示模块的时间戳。  默认值为 `no`。  
  
 \/Version:`yes|no`  
 可选。  指定是否显示模块的版本。  默认值为 `no`。  
  
## 备注  
  
## 示例  
 此示例列出当前进程的模块名称、地址和时间戳。  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [如何：使用“模块”窗口](../../debugger/how-to-use-the-modules-window.md)