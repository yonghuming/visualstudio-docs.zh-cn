---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Shutdown** 选项会等待任何当前分析的进程结束或分离，然后关闭探查器并关闭分析数据文件。  **Shutdown** 选项必须是分析运行的最后一个命令。  
  
 如果没有指定超时参数，则 **Shutdown** 将无限期等待。  如果指定了超时参数，则此选项将在指定的秒数后返回，而不会关闭探查器或数据文件。  
  
 **Shutdown** 选项必须是命令行中指定的唯一选项。  
  
## 语法  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### 参数  
 `Timeout`  
 -   （可选）如果指定，则此选项将在指定的秒数后返回，而不会关闭探查器或分析数据文件。  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)