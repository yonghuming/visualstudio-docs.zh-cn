---
title: "如何：使用命令行将探查器附加到 ASP.NET Web 应用程序以收集内存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到 ASP.NET Web 应用程序以收集内存数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具将探查器附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，以及如何收集有关 .NET Framework 内存分配数量和大小的数据。  也可以收集有关 .NET Framework 内存对象生存期的数据。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要从 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序收集性能数据，请在承载 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序的计算机上使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化相应的环境变量。  您必须重新启动计算机以配置 Web 服务器进行分析。  
  
 然后，使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md) 工具将探查器附加到承载您的网站的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  在将探查器附加到应用程序时，可以暂停和继续数据收集。  
  
 若要结束分析会话，必须从应用程序分离探查器并显式关闭探查器。  在大多数情况下，建议在会话结束时清除分析环境变量。  
  
## 附加探查器  
  
#### 将探查器附加到 ASP.NET Web 应用程序  
  
1.  打开命令提示符窗口。  
  
2.  初始化分析环境变量。  键入：  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   **\/globalsamplegc** 和 **\/globalsamplegclife** 选项指定要收集的内存数据类型。  
  
         指定下列选项中的一个且仅指定一个。  
  
        |选项|描述|  
        |--------|--------|  
        |**\/globalsamplegc**|启用对内存分配数据的收集。|  
        |**\/globalsamplegclife**|启用对内存分配数据和对象生存期数据的收集。|  
  
    -   **\/samplelineoff** 选项禁用将收集的数据分配到特定源代码行。  如果指定此选项，则在函数级别分配数据。  
  
3.  重新启动计算机以设置新的环境配置。  
  
4.  打开命令提示符窗口。  如有必要，设置探查器路径环境变量。  
  
5.  启动探查器。  键入：  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start:sample** 选项初始化探查器。  
  
    -   **\/output:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:sample** 选项一起使用。  
  
    > [!NOTE]
    >  ASP.NET 应用程序通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有 ASP.NET 工作进程的帐户的域名和用户名。  如果该进程以已登录用户之外的用户身份运行，则需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。  如果 ASP.NET 应用程序在其他会话中运行，则需要此选项。  会话标识符列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|指定探查器初始化期间在返回错误之前等待的秒数。  如果未指定 `Interval`，则探查器将无限期等待。  默认情况下，**\/start** 将立即返回。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
6.  通过典型方式启动 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  
  
7.  将探查器附加到 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  键入：  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   进程 ID `(PID)` 指定 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程的进程 ID 或进程名称。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
    -   **\/targetclr:** `Version`  指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。  
  
## 控制数据收集  
 在应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向探查器数据文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下 **VSPerfCmd** 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) `PID` 所指定的进程的数据收集。|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|**\/attach** 开始对由进程 ID 或进程名称指定的进程收集数据。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，必须从 Web 应用程序分离探查器。  通过重新启动 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程，或者通过调用 **VSPerfCmd \/detach** 选项，可以停止从使用采样方法分析的应用程序收集数据。  然后，可以调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项，关闭探查器和分析数据文件。  **VSPerfClrEnv \/globaloff** 命令清除分析环境变量，但只有重新启动计算机之后才会重置系统配置。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器：  
  
    -   键入 **VSPerfCmd** [\/detach](../profiling/detach.md)  
  
         \- 或 \-  
  
    -   关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  键入：  
  
     **IISReset \/stop**  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd \/shutdown**  
  
3.  （可选）清除分析环境变量。  键入：  
  
     **VSPerfCmd \/globaloff**  
  
4.  重新启动计算机。  如有必要，重新启动 Internet Information Services \(IIS\)。  键入：  
  
     **IISReset \/start**  
  
## 请参阅  
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)