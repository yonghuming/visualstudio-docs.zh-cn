---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe 的 **Sys** 选项设置按系统调用事件（被分析的应用程序中对操作系统的函数调用）采样的分析事件，根据需要还可以将采样间隔内的系统调用数从默认值 10 改为其他值。  
  
 只能在同时包含 **Launch** 或 **Attach** 选项的命令行中使用 **Sys**。  
  
 默认情况下，将探查器采样事件设置为处理器时钟周期，并将采样间隔设置为 10,000,000。  使用 **Timer**、**PF**、**Sys** 和 **Counter** 选项可以设置采样事件和采样间隔。  **GC** 选项在每次发生分配和垃圾回收事件时收集 .NET 内存数据。  在命令行中只能指定这些选项中的一个。  
  
 只能在包含 **Launch** 或 **Attach** 选项的第一个命令行中设置采样事件和采样间隔。  
  
## 语法  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### 参数  
 `Events`  
 一个整数值，指定采样间隔内系统调用事件的数量。  如果未指定 `Events`，则将间隔设置为 10。  
  
## 必需选项  
 **Sys** 要求使用以下选项之一。  
  
 **Launch:** `AppName`  
 启动探查器以及由 `AppName` 指定的应用程序。  
  
 **Attach:** `PID`  
 将探查器附加到 `PID` 指定的进程。  
  
## 无效选项  
 不能在 **Sys** 所在的命令行中指定以下选项：  
  
 **PF**\[**:**`Events`\]  
 将采样事件设置为页面错误，根据需要还可以将采样间隔设置为 `Events`。  默认 PF 间隔为 10。  
  
 **Timer**\[**:**`Cycles`\]  
 将采样事件设置为处理器时钟周期，还可以选择将采样间隔设置为 `Cycles`。  默认 Timer 间隔为 10,000,000。  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 将采样事件设置为 `Name` 指定的 CPU 性能计数器，并将采样间隔设置为 `Reload`。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 收集 .NET 内存数据。  默认情况 \(**Allocation**\) 下，每次发生内存分配事件时都收集数据。  如果指定 **Lifetime** 参数，则每次发生垃圾回收事件时也收集数据。  
  
## 示例  
 本示例演示如何将探查器采样事件设置为系统调用，以及如何将采样间隔设置为每个示例 20 个调用。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)