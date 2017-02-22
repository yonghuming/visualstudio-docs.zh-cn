---
title: "标记 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Mark** 选项将指定的信息插入分析数据文件中。  可以在单独的 VSPerfReport 报告中或探查器 UI 的“标记报告”视图中列出标记。  **Mark** 可用于指定报告中的起点和终点以及查看筛选器。  
  
 **Mark** 选项必须是命令行中指定的唯一选项。  
  
## 语法  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### 参数  
 `MarkID`  
 作为探查器视图和报告中的标记 ID 列出的用户定义的整数。  `MarkID` 不必是唯一的。  
  
 `MarkName`  
 （可选）作为探查器视图和报告中的“标记名称”列出的用户定义的字符串。  如果未指定 `MarkName`，则列出的标记的“标记名称”字段为空。  将包含空格或正斜杠（“\/”）的字符串用引号引起来。  
  
## 示例  
 此示例插入 ID 为 123、标记名称为“TestMark”的标记。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)