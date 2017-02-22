---
title: "如何：使用命令行将探查器附加到 .NET 服务，以收集并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到 .NET 服务，以收集并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具将探查器附加到 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服务，以及如何使用采样方法收集进程和线程并发数据。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  分析工具的命令行工具位于 Visual Studio 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，同时提供这些工具的 64 位和 32 位版本。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 要收集并发数据，你需要将探查器附加到服务进程。  在将探查器附加到服务时，可以暂停和继续数据收集。  若要结束分析会话，必须将探查器与服务断开并且必须显式关闭探查器。  在大多数情况下，建议在会话结束时清除分析环境变量。  
  
## 附加探查器  
  
#### 将探查器附加到 .NET Framework 服务  
  
1.  安装服务。  
  
2.  打开命令窗口。  
  
3.  初始化分析环境变量。  键入：  
  
     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **\/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** 启用采样。  
  
    -   **\/samplelineoff** 禁用将收集的数据分配到特定源代码行。  指定此选项时，数据只分配给函数。  
  
4.  重新启动计算机。  
  
5.  启动探查器。  键入：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start** 选项一起使用。  
  
    > [!NOTE]
    >  服务通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有所分析进程的帐户的域名和用户名。  仅当运行进程的用户不是已登录用户时，才需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他会话中的进程分析。  如果服务在其他会话中运行，则需要此选项。  会话 ID 列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
6.  如有必要，请启动相应服务。  
  
7.  将探查器附加到服务。  键入：  
  
     **VSPerfCmd \/attach:** `PID` \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` 指定服务的进程 ID 或进程名称。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
    -   **targetclr:** `Version` 指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。  可选。  
  
## 控制数据收集  
 在服务运行期间，通过使用 VSPerfCmd.exe 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下 **VSPerfCmd** 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由进程 ID 或进程名称指定的进程收集数据。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
-   还可以使用 **VSPerfCmd.exe** [\/mark](../profiling/mark.md) 选项在数据文件中插入分析标记。  **\/mark** 命令添加一个标识符、一个时间戳和一个可选的用户定义的文本字符串。  标记可用于筛选探查器报告和数据视图中的数据。  以下 VSPerfCmd 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
## 结束分析会话  
 探查器未在收集数据时，才能结束分析会话。  通过停止服务，或调用 **VSPerfCmd \/detach** 选项，可以停止从使用并发方法分析的应用程序中收集数据。  然后，可以调用 **VSPerfCmd \/shutdown** 选项关闭探查器并关闭分析数据文件。  **VSPerfClrEnv \/globaloff** 命令清除分析环境变量，但只有重新启动计算机之后才会重置系统配置。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器。  
  
    -   停止服务。  
  
         \- 或 \-  
  
    -   键入 **VSPerfCmd \/detach.**  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)