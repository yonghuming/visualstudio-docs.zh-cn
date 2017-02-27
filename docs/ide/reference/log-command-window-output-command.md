---
title: "“日志命令窗口输出”命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "“日志命令窗口输出”命令"
  - "View.LogCommandWindowOutput 命令"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# “日志命令窗口输出”命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将**“命令”**窗口的所有输入和输出复制到文件中。  
  
## 语法  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## 参数  
 `filename`  
 可选。  日志文件的名称。  默认情况下，该文件在用户的配置文件夹中创建。  如果该文件名已经存在，日志将追加到该现有文件的结尾处。  如果未指定文件，将使用上次指定的文件。  如果不存在上一个文件，则创建名为 cmdline.log 的默认日志文件。  
  
> [!TIP]
>  若要更改日志文件的保存位置，请输入文件的完整路径；如果路径中包含任何空格，请用引号将其引起来。  
  
## 开关  
 \/on  
 可选。  在指定文件中启动**“命令”**窗口的日志，并将新信息追加到该文件中。  
  
 \/off  
 可选。  停止**“命令”**窗口的日志。  
  
 \/overwrite  
 可选。  如果 `filename` 参数中指定的文件与某个现有文件匹配，则覆盖该现有文件。  
  
## 备注  
 如果未指定文件，默认情况下创建文件 cmdline.log。  默认情况下，此命令的别名是 Log。  
  
## 示例  
 此示例创建新的日志文件 cmdlog 并启动命令日志。  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 此示例停止记录命令。  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 此示例继续在以前使用的日志文件中记录命令。  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## 请参阅  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [“查找\/命令”框](../../ide/find-command-box.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)