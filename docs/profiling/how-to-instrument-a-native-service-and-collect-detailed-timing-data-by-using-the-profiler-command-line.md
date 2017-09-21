---
title: "如何：使用探查器命令行检测本机服务并收集详细计时数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用探查器命令行检测本机服务并收集详细计时数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具检测本机 \(C\/C\+\+\) 服务并收集详细计时数据。  
  
> [!NOTE]
>  如果一个服务在计算机启动之后无法重新启动，这样的服务只能在操作系统启动时启动，则无法使用检测方法分析该服务。  
>   
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，同时提供这些工具的 64 位和 32 位版本。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量中，或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要使用检测方法从本机服务收集详细计时数据，应使用 [VSInstr.exe](../profiling/vsinstr.md) 工具生成该组件的检测版本。  然后，将该服务的非检测版本替换为检测版本，确保将该服务配置为手动启动。  然后启动探查器。  
  
 在启动该服务时，会自动将计时数据收集到数据文件中。  在分析会话过程中可以暂停和继续数据收集。  
  
 若要结束分析会话，可关闭该服务，然后显式关闭探查器。  
  
## 将应用程序与探查器一起启动  
  
#### 开始分析本机服务  
  
1.  打开命令提示符窗口。  
  
2.  使用 **VSInstr** 工具生成该服务版本的检测版本。  
  
3.  使用检测版本替换原始版本。  在 Windows 服务控制管理器中，确保将该服务的“启动类型”设置为“手动”。  
  
4.  启动探查器。  键入：  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   **\/start:trace** 选项初始化探查器。  
  
    -   **\/output:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:trace** 选项一起使用。  
  
    > [!NOTE]
    >  ASP.NET 应用程序通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有 ASP.NET 工作进程的帐户的域名和用户名。  如果该进程以已登录用户之外的用户身份运行，则需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。  如果 ASP.NET 应用程序在其他会话中运行，则需要此选项。  会话 ID 列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|指定探查器初始化期间在返回错误之前等待的秒数。  如果未指定 `Interval`，则探查器将无限期等待。  默认情况下，**\/start** 将立即返回。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|若要启动探查器而暂停数据收集，请将 **\/globaloff** 选项添加到 **\/start** 命令行。  使用 **\/globalon** 可继续分析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|从 Config 中所指定的处理器性能计数器收集信息。  计数器信息将添加到在每个分析事件中收集的数据中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
5.  从服务控制管理器启动服务。  
  
## 控制数据收集  
 在服务运行时，可以使用 **VSPerfCmd.exe** 选项启动和停止向探查器数据文件写入数据。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭服务阶段）的数据。  
  
#### 开始和停止数据收集  
  
-   以下 **VSPerfCmd** 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|开始 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 线程 ID \(`TID`\) 所指定的线程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，请停止运行所检测的组件的服务，然后调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项关闭探查器，并关闭分析数据文件。  
  
#### 结束分析会话  
  
1.  从服务控制管理器停止服务。  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd \/shutdown**  
  
3.  使用检测模块替换原始模块。  如有必要，重新配置服务的“启动类型”。  
  
## 请参阅  
 [分析服务](../profiling/command-line-profiling-of-services.md)   
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)