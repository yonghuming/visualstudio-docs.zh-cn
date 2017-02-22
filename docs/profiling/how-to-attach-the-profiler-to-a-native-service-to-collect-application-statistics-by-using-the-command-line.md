---
title: "如何：使用命令行将探查器附加到本机服务，以收集应用程序统计信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到本机服务，以收集应用程序统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具将探查器附加到本机服务，以及如何使用采样方法收集性能统计信息。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，同时提供这些工具的 64 位和 32 位版本。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量中，或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 在将探查器附加到服务时，可以暂停和继续数据收集。  
  
 若要结束分析会话，必须将探查器与服务断开，且显式关闭探查器。  
  
## 将应用程序与探查器一起启动  
 若要将探查器附加到本机服务，可以使用 **VSPerfCmd.exe** [\/start](../profiling/start.md) 和 [\/attach](../profiling/attach.md) 选项初始化探查器并将其附加到目标应用程序。  可以在单个命令行上指定 **\/start** 和 **\/attach** 及其各自的选项。  还可以添加 [\/globaloff](../profiling/globalon-and-globaloff.md) 选项，以在目标应用程序启动时暂停数据收集。  然后，可以使用 [\/globalon](../profiling/globalon-and-globaloff.md) 开始收集数据。  
  
#### 将探查器附加到本机服务  
  
1.  如有必要，请启动相应服务。  
  
2.  打开命令提示符窗口。  
  
3.  启动探查器。  键入：  
  
     **VSPerfCmd \/start:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start:sample** 选项初始化探查器。  
  
    -   **\/output:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:sample** 选项一起使用。  
  
    > [!NOTE]
    >  服务通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有所分析进程的帐户的域名和用户名。  仅当运行进程的用户不是已登录用户时，才需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他会话中的进程分析。  如果应用程序在其他会话中运行，则需要此选项。  会话 ID 列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
4.  将探查器附加到服务。  键入：  
  
     **VSPerfCmd \/attach:** `PID` \[`Sample Event`\]  
  
     `PID` 指定目标应用程序的进程 ID。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
     默认情况下，每经过 10,000,000 个非暂停处理器时钟周期，就对性能数据进行一次采样。  这近似于在 1GH 处理器上每隔 10 秒采样一次。  通过指定下列选项之一，可以更改时钟周期间隔或指定其他采样事件。  
  
    |采样事件|描述|  
    |----------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|将采样间隔更改为 `Interval` 所指定的非暂停时钟周期数。|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|将采样事件更改为页面错误。  如果指定了 `Interval`，则设置两次样本之间的页面错误数。  默认值为 10。|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|将采样事件更改为进程对操作系统内核的系统调用 \(syscall\)。  如果指定了 `Interval`，则设置两次样本之间的调用数。  默认值为 10。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|将采样事件更改为处理器性能计数器，并将间隔更改为 `Config` 中指定的间隔。|  
  
## 控制数据收集  
 在目标应用程序运行时，可以使用 **VSPerfCmd.exe** 选项启动和停止向探查器数据文件写入数据。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下 **VSPerfCmd** 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |**\/attach:** {`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由进程 ID 或进程名称指定的进程收集数据。  **\/detach** 停止对指定进程的数据收集，如果未指定某一进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，必须将探查器与服务断开然后显式关闭探查器。  通过停止本机服务或调用 **VSPerfCmd \/detach** 选项，可以断开正在使用采样方法分析的本机服务。  然后，可以调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项，关闭探查器和分析数据文件。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器：  
  
    -   停止服务。  
  
         \- 或 \-  
  
    -   键入 **VSPerfCmd \/detach**  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd \/shutdown**  
  
## 请参阅  
 [分析服务](../profiling/command-line-profiling-of-services.md)   
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)