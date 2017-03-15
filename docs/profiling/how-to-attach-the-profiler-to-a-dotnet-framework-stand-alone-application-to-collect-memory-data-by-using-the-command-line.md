---
title: "如何：使用命令行将探查器附加到 .NET Framework 独立应用程序以收集内存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到 .NET Framework 独立应用程序以收集内存数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]分析工具的命令行工具将探查器附加到正在运行的 .NET Framework 独立（客户端）应用程序，以及如何收集内存数据。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要附加到 .NET Framework 应用程序并收集内存数据，必须使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化相应的环境变量，然后才能启动目标应用程序。  将探查器附加到应用程序时，可以使用 **VSPerfCmd.exe** 工具暂停和继续数据收集。  
  
 若要结束分析会话，必须将探查器与所有被分析进程分离，并且必须显式关闭探查器。  在大多数情况下，建议在会话结束时清除分析环境变量。  
  
## 附加探查器  
  
#### 将探查器附加到正在运行的 .NET Framework 应用程序  
  
1.  打开命令提示符窗口。  
  
2.  初始化分析环境变量。  键入：  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   **\/samplegc** 和 **\/samplegclife** 选项指定是仅收集内存分配数据，还是同时收集内存分配数据和对象生存期数据。  必须指定一个且仅指定一个选项。  
  
        |选项|说明|  
        |--------|--------|  
        |**\/samplegc**|仅收集内存分配数据。|  
        |**\/samplegclife**|同时收集内存分配数据和对象生存期数据。|  
  
    -   **\/samplelineoff** 选项禁用源代码行号数据的收集。  
  
3.  启动探查器。  键入：  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:sample** 选项初始化探查器。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:sample** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有所分析进程的帐户的域名和用户名。  仅当运行进程的用户不是已登录用户时，才需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|启用其他会话中的进程分析。  如果应用程序在其他会话中运行，则需要此选项。  会话标识符列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
  
4.  如有必要，通过典型方式启动目标应用程序。  
  
5.  将探查器附加到目标应用程序。  键入：  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` 指定目标应用程序的进程 ID。  `ProcessName` 指定进程的名称。  请注意，如果指定 `ProcessName`，但有多个同名进程在运行，则结果是不可预知的。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
    -   **\/targetclr:** `Version` 指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。  可选。  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) `PID` 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由 `PID` 或进程名称 \(ProcName\) 指定的进程进行数据收集。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，必须将探查器与所有被分析进程分离，并且必须显式关闭探查器。  通过关闭应用程序或调用 **VSPerfCmd \/detach** 选项，可以从使用采样方法分析的应用程序分离探查器。  然后，可以调用 **VSPerfCmd \/shutdown** 选项，关闭探查器和分析数据文件。  **VSPerfClrEnv \/off** 命令清除分析环境变量。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器：  
  
    -   键入 **VSPerfCmd \/detach**  
  
         \- 或 \-  
  
    -   关闭目标应用程序。  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  （可选）清除分析环境变量。  键入：  
  
     **VSPerfCmd \/off**  
  
## 请参阅  
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)