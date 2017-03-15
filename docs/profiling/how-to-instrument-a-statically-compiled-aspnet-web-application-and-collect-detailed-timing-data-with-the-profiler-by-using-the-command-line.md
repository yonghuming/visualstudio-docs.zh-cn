---
title: "如何：使用命令行通过探查器检测静态编译的 ASP.NET Web 应用程序并收集详细计时数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行通过探查器检测静态编译的 ASP.NET Web 应用程序并收集详细计时数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具检测预编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 组件或网站，以及如何收集详细的计时数据。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  将层交互数据添加到运行的分析需要使用分析工具的特定程序。  请参见 [收集层交互数据](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
  
 若要使用检测方法从 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 组件收集详细计时数据，请使用 [VSInstr.exe](../profiling/vsinstr.md) 工具生成组件的受检测版本。  在承载该组件的计算机上，将该组件的非检测版本替换为受检测的版本。  然后使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化全局分析环境变量并重新启动主机。  然后启动探查器。  
  
 在执行检测组件时，会自动将计时数据收集到数据文件中。  在分析会话过程中可以暂停和继续数据收集。  
  
 若要结束分析会话，请关闭承载该组件的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程，然后显式关闭探查器。  在大多数情况下，建议在会话结束时清除分析环境变量。  
  
## 开始分析  
  
#### 检测 ASP.NET Web 组件并开始分析  
  
1.  打开命令提示符窗口。  
  
2.  使用 **VSInstr** 工具生成目标应用程序的受检测版本。  如有必要，将 ASP.NET 主机上的应用程序二进制文件替换为受检测的二进制文件。  
  
3.  初始化 .NET 分析环境变量。  在“命令提示符”窗口中，键入：  
  
     **VSPerfClrEnv \/globaltraceon**  
  
4.  重新启动计算机。  
  
5.  打开命令提示符窗口。  如有必要，请设置探查器工具路径。  
  
6.  启动探查器。  键入：  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** 选项初始化探查器。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:trace** 选项一起使用。  
  
    > [!NOTE]
    >  ASP.NET 应用程序通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有 ASP.NET 工作进程的帐户的域名和用户名。  如果该进程以已登录用户之外的用户身份运行，则需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。  如果 ASP.NET 应用程序在其他会话中运行，则需要此选项。  会话标识符列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|若要启动探查器而暂停数据收集，请将 **\/globaloff** 选项添加到 **\/start** 命令行。  使用 **\/globalon** 可继续分析。|  
  
7.  打开包含受检测组件的网站。  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|开始 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 线程 ID \(`TID`\) 所指定的线程的数据收集。|  
  
## 结束分析会话  
 若要结束分析会话，请关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，然后使用 Internet Information Services \(IIS\) **IISReset** 命令关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  调用 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 选项关闭探查器并关闭分析数据文件。  
  
 **VSPerfClrEnv \/globaloff** 命令清除分析环境变量。  必须重新启动计算机，才能应用新的环境设置。  
  
#### 结束分析会话  
  
1.  关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  
  
2.  关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程。  键入：  
  
     **IISReset \/stop**  
  
3.  关闭探查器。  键入：  
  
     **VSPerfCmd \/shutdown**  
  
4.  （可选）。  清除分析环境变量。  键入：  
  
     **VSPerfCmd \/globaloff**  
  
5.  重新启动计算机。  
  
## 请参阅  
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)