---
title: "ThreadOn 和 ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ThreadOn 和 ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **ThreadOff** 和 **ThreadOn** 子命令只能在使用检测方法的命令行分析会话中使用。  **ThreadOff** 和 **ThreadOn** 可暂停和恢复指定进程的分析。  **ThreadOff** 可停止分析线程，而 **ThreadOn** 则可启动分析线程。  
  
 在大多数情况下，指定 **ThreadOn** 或 **ThreadOff** 作为 VSPerfCmd.exe 命令行中仅有的选项，但可以将这些选项与 **GlobalOn**、**GlobalOff**、**ProcessOn** 和 **ProcessOff** 子命令组合在一起。  
  
 **ThreadOn** 和 **ThreadOff** 子命令与控制命令行分析会话中所有进程的数据收集的 **GlobalOn** 和 **GlobalOff** 子命令交互，并与控制指定进程的数据收集的 **ProcessOn** 和 **ProcessOff** 子命令交互。  
  
 **ThreadOff** 和 **ThreadOn** 子命令还会影响探查器 API 函数所操作的线程启动\/停止计数。  
  
-   **ThreadOff** 将线程启动\/停止计数立即设置为 0，因此暂停分析。  
  
-   **ThreadOn** 将线程启动\/停止计数立即设置为 1，因此继续分析。  
  
 有关更多信息，请参见 [分析工具 API](../profiling/profiling-tools-apis.md)。  
  
## 语法  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### 参数  
 `TID`  
 要启动或停止的线程的整数标识符。  
  
## 有效选项  
 可以在还包含以下子命令的命令行上指定 **ThreadOn** 和 **ThreadOff**。  
  
 **Start:** `Method`  
 初始化命令行分析会话并设置指定的分析方法。  
  
 **GlobalOff**&#124;**GlobalOn**  
 停止或启动对命令行分析会话中所有进程的分析。  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 停止或启动对指定进程的分析。  
  
## 示例  
 在此示例中，**ThreadOff** 子命令用于停止收集分析数据，以便仅收集应用程序启动数据。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)