---
title: "Launch | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Launch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Launch** 选项使用采样方法启动探查器，它还启动指定的应用程序。  
  
 若要使用 **Launch** 选项，必须在 **Start** 选项中指定 **Sample** 方法。  
  
## 语法  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### 参数  
 `AppName`  
 要启动的应用程序的名称。  支持当前目录中的完整路径和部分路径。  
  
## 有效选项  
 在单个命令行上，可以将以下 VSPerfCmd 选项与 **Launch** 选项一起使用。  
  
 **Start:** `Method`  
 初始化命令行探查器会话并设置指定的分析方法。  
  
 **GlobalOn**以及**GlobalOff**  
 恢复 \(**GlobalOn**\) 或暂停 \(**GlobalOff**\) 分析，但不结束分析会话。  
  
 **ProcessOn:** `PID` 和**ProcessOff**:`PID`  
 恢复 \(**ProcessOn**\) 或暂停 \(**ProcessOff**\) 指定进程的分析。  
  
 **TargetCLR**  
 指定在分析会话中加载了多个版本的 .NET Framework 公共语言运行时 \(CLR\) 时，要分析的 .NET Framework CLR 的版本。  默认情况下分析加载的第一个版本。  
  
## 专有选项  
 以下选项只能与 **Launch** 选项一起使用。  
  
 **Console**  
 在新窗口中启动指定的命令行应用程序。  
  
 **Args:** `ArgList`  
 指定要传递给应用程序的参数的列表。  
  
 **LineOff**  
 禁用收集行级分析数据。  
  
## 采样选项  
 可在 **Launch** 命令行中指定下面某个采样间隔选项。  默认的采样间隔是 10,000,000 个处理器时钟周期。  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 指定采样间隔的数目和类型。  
  
-   **Timer** \- 每 `Cycles` 个非暂停处理器时钟周期进行一次采样。  如果未指定 `Cycles`，则使用 10,000,000 个周期。  
  
-   **PF** \- 每 `Events` 个页面错误进行一次采样。  如果未指定 `Events`，则使用 10 个页面错误。  
  
-   **Sys** \- 每 `Events` 次操作系统调用进行一次采样。  如果未指定 `Events`，则使用 10 次系统调用。  
  
-   **Counter** \- 每 `Reload` 个 `Name` 所指定的 CPU 性能计数器进行一次采样。  可以选择使用 `FriendlyName` 来指定在探查器报告中用作列标题的字符串。  
  
-   **GC** \- 收集 .NET 内存数据。  默认情况 \(**allocation**\) 下，每次发生内存分配事件时都收集数据。  如果指定 **lifetime** 参数，则每次发生垃圾回收事件时也收集数据。  
  
## 示例  
 此示例演示如何使用 **Launch** 启动应用程序。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)