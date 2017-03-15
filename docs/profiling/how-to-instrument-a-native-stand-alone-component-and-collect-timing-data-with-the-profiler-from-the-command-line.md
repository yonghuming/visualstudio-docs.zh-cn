---
title: "如何：从命令行用探查器检测本机独立组件并收集计时数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：从命令行用探查器检测本机独立组件并收集计时数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具检测本机组件（如 C\+\+ .exe 或 .dll 文件）以及如何收集详细计时数据。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要使用检测方法从组件收集详细计时数据，请使用 [VSInstr.exe](../profiling/vsinstr.md) 工具生成组件的受检测版本。  然后启动探查器。  在执行检测组件时，会自动将计时数据收集到数据文件中。  在分析会话过程中可以暂停和继续数据收集。  
  
 若要结束分析会话，请关闭目标应用程序，然后显式关闭探查器。  
  
## 启动分析会话  
  
#### 使用检测方法启动分析  
  
1.  打开命令提示符窗口。  
  
2.  使用 **VSInstr** 工具生成目标应用程序的受检测版本。  
  
3.  启动探查器。  键入：  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** 选项初始化探查器。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列一个或多个选项与 **\/start:trace** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有所分析进程的帐户的域名和用户名。  仅当运行进程的用户不是已登录用户时，才需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他会话中的进程分析。  如果应用程序在其他会话中运行，则需要此选项。  会话标识符列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|启动探查器，同时暂停数据收集。  使用 [\/globalon](../profiling/globalon-and-globaloff.md) 可继续分析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|从 `Config` 中所指定的处理器性能计数器收集信息。  计数器信息将添加到在每个分析事件中收集的数据中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
4.  通过典型方式启动目标应用程序。  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止由进程 ID \(`PID`\) 指定的进程的 \(**\/processoff**\) 数据收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|开始 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 线程 ID \(`TID`\) 所指定的线程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，请关闭运行所检测的组件的应用程序，然后调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项关闭探查器，并关闭分析数据文件。  
  
#### 结束分析会话  
  
1.  关闭目标应用程序。  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd \/shutdown**  
  
## 请参阅  
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)