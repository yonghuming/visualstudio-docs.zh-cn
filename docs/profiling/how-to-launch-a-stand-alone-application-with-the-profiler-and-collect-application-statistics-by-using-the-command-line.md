---
title: "如何：使用命令行通过探查器启动独立应用程序并收集应用程序统计信息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行通过探查器启动独立应用程序并收集应用程序统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具启动独立（客户端）应用程序，以及如何使用采样方法收集性能统计信息。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
>   
>  将层交互数据添加到运行的分析需要使用分析工具的特定程序。  请参见[收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
 若要使用探查器命令行工具，必须将路径添加到命令提示符窗口的 PATH 环境变量中，或添加到命令本身。  可以在 Visual Studio 中运行时从 Visual Studio 命令窗口安装的计算机的分析工具。  
  
1.  如果运行在安装 Visual Studio 的计算机的分析工具 Visual Studio 命令窗口设置正确的路径。  在工具  菜单中，选择使用命令提示  
  
> [!NOTE]
>  分析工具的命令行工具位于 Visual Studio 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将路径添加到命令提示符窗口的 PATH 环境变量中，或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 将应用程序与探查器一起启动  
 若要使用探查器来启动目标应用程序，请使用 VSPerfCmd **\/start** 和 **\/launch** 选项初始化探查器并启动应用程序。  可以在单个命令行上指定 **\/start** 和 **\/launch** 及其各自的选项。  
  
 还可以添加 **\/globaloff** 选项，以在目标应用程序启动时暂停数据收集。  然后，可以使用 **\/globalon** 开始收集数据。  
  
#### 使用探查器启动应用程序  
  
1.  打开命令提示符窗口。  
  
2.  启动探查器。  键入：  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:sample** 选项初始化探查器。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:sample** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
3.  启动目标应用程序。  键入：**VSPerfCmd \/launch:**`appName` \[`Options`\] \[`Sample Event`\]  
  
     可以将下列一个或多个选项与 **\/launch** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|指定一个字符串，该字符串包含要传递给目标应用程序的命令行参数。|  
    |[\/console](../profiling/console.md)|在单独的窗口中启动目标命令行应用程序。|  
  
     默认情况下，每经过 10,000,000 个非暂停处理器时钟周期，就对性能数据进行一次采样。  这近似于对 1GHz 处理器每隔 10 秒采样一次。  通过指定下列选项之一，可以更改时钟周期间隔或指定其他采样事件。  
  
    |采样事件|描述|  
    |----------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|将采样间隔更改为 `Interval` 所指定的非暂停时钟周期数。|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|将采样事件更改为页面错误。  如果指定了 `Interval`，则设置两次样本之间的页面错误数。  默认值为 10。|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[**:**`Interval`\]|将采样事件更改为进程对操作系统内核的系统调用 \(syscall\)。  如果指定了 `Interval`，则设置两次样本之间的调用数。  默认值为 10。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|将采样事件更改为处理器性能计数器，并将间隔更改为 `Config` 中指定的间隔。|  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向探查器数据文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由 `PID` 或进程名称 \(ProcName\) 指定的进程收集数据。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，不得将探查器附加到任何被分析的进程，并且必须显式关闭探查器。  通过关闭应用程序或调用 **VSPerfCmd \/detach** 选项，可以从使用采样方法分析的应用程序分离探查器。  然后，可以调用 **VSPerfCmd \/shutdown** 选项，关闭探查器和分析数据文件。  **VSPerfClrEnv \/off** 命令清除分析环境变量。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器：  
  
    -   关闭目标应用程序。  
  
         \- 或 \-  
  
    -   键入 **VSPerfCmd \/detach**  
  
2.  关闭探查器。  键入：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 请参阅  
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)