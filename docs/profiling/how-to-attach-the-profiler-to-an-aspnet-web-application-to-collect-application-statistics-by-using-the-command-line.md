---
title: "如何：使用命令行将探查器附加到 ASP.NET Web 应用程序中以收集应用程序统计信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到 ASP.NET Web 应用程序中以收集应用程序统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具将探查器附加到 ASP.NET Web 应用程序，以及如何使用采样方法收集性能统计信息。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
>   
>  将层交互数据添加到运行的分析需要使用分析工具的特定程序。  请参见 [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
>   
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要从 ASP.NET Web 应用程序中收集性能数据，必须初始化相应的环境变量并重新启动承载 ASP.NET 应用程序的计算机，才能配置 Web 服务器进行分析。  
  
 然后将探查器附加到承载您的网站的 ASP.NET 辅助进程。  在将探查器附加到应用程序时，可以暂停和继续数据收集。  
  
 若要结束分析会话，必须将探查器与被分析的应用程序分离，并且必须显式关闭探查器。  在大多数情况下，建议在会话结束时清除分析环境变量。  
  
## 启动探查器并将其附加到 ASP.NET Web 应用程序  
  
#### 将探查器附加到 ASP.NET Web 应用程序  
  
1.  打开命令提示符窗口。  
  
2.  初始化分析环境变量。  键入：  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** 启用采样。  
  
    -   **\/samplelineoff** 禁用将收集的数据分配到特定源代码行。  指定此选项时，数据只分配给函数。  
  
3.  重新启动计算机。  
  
4.  启动探查器。  键入：**VSPerfCmd** [\/start](../profiling/start.md)**:sample** [\/output](../profiling/output.md)**:**`OutputFile`\[`Options`\]  
  
    -   **\/start:sample** 选项初始化探查器。  
  
    -   **\/output:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可将下列任意一个选项与 **\/start:sample** 选项一起使用。  
  
    > [!NOTE]
    >  ASP.NET 应用程序通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有 ASP.NET 工作进程的帐户的域名和用户名。  如果该进程以已登录用户之外的用户身份运行，则需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。  如果 ASP.NET 应用程序在其他会话中运行，则需要此选项。  会话标识符列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
5.  通过典型方式启动 ASP.NET Web 应用程序。  
  
6.  将探查器附加到 ASP.NET 辅助进程。  键入：**VSPerfCmd** [\/attach](../profiling/attach.md)**:**{`PID` &#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` 指定 ASP.NET 辅助进程的进程 ID；`ProcName` 指定辅助进程的名称。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID 和名称。  
  
    -   默认情况下，每经过 10,000,000 个非暂停处理器时钟周期，就对性能数据进行一次采样。  这近似于每秒对 1GHz 处理器采样 100 次。  通过指定下列 **VSPerfCmd** 选项之一，可以更改时钟周期间隔或指定其他采样事件。  
  
    |采样事件|描述|  
    |----------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|将采样间隔更改为 `Interval` 所指定的非暂停时钟周期数。|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|将采样事件更改为页面错误。  如果指定了 `Interval`，则设置两次样本之间的页面错误数。  默认值为 10。|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|将采样事件更改为进程对操作系统内核的系统调用 \(syscall\)。  如果指定了 `Interval`，则设置两次样本之间的调用数。  默认值为 10。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|将采样事件更改为处理器性能计数器，并将间隔更改为 `Config` 中指定的间隔。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。|  
  
    -   **targetclr:** `Version` 用于在应用程序中加载了多个版本的 CLR 时指定要对哪一运行时版本进行分析。  可选。  
  
## 控制数据收集  
 在应用程序运行期间，可以使用 **VSPerfCmd.exe** 选项开始和停止向文件写入数据，从而控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下 **VSPerfCmd** 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` **\/processoff:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) `PID` 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由 `PID` 或进程名称 \(ProcName\) 指定的进程收集数据。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，请关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，然后使用 Internet Information Services \(IIS\) **IISReset** 命令关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项关闭探查器并关闭分析数据文件。  
  
 **VSPerfClrEnv \/globaloff** 命令清除分析环境变量。  必须重新启动计算机，才能应用新的环境设置。  
  
 **VSPerfClrEnv \/globaloff** 命令清除分析环境变量，但只有重新启动计算机之后才会重置系统配置。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器：  
  
    -   键入 **VSPerfCmd \/detach**  
  
         \- 或 \-  
  
    -   关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  
  
2.  关闭探查器。  键入：**VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
3.  （可选）清除分析环境变量。  键入：  
  
     **VSPerfCmd \/globaloff**  
  
4.  重新启动计算机。  
  
## 请参阅  
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)