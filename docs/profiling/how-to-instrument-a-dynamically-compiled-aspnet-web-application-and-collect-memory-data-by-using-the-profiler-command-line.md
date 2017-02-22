---
title: "如何：使用探查器命令行检测动态编译的 ASP.NET Web 应用程序并收集内存数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用探查器命令行检测动态编译的 ASP.NET Web 应用程序并收集内存数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具，通过检测分析方法收集动态编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序的详细 .NET 内存分配和对象生存期数据。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，同时提供这些工具的 64 位和 32 位版本。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量中，或添加到命令本身。  有关更多信息，请参见[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要从 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序收集性能数据，请修改目标应用程序的 web.config 文件，以使 [VSInstr.exe](../profiling/vsinstr.md) 工具可以检测动态编译的应用程序文件。  然后，使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具，通过设置相应的环境变量来配置承载 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序的服务器并启用 .NET 内存分析，然后重新启动计算机。  
  
 若要收集数据，请启动探查器，然后运行目标应用程序。  将探查器附加到应用程序的同时，可以暂停和继续数据收集。收集了适当的数据后，请关闭应用程序，关闭 Internet Information Services \(IIS\) 辅助进程，然后关闭探查器。  
  
 完成分析工作后，请将 web.config 文件和 Web 服务器还原到其原始状态。  
  
## 配置 ASP.NET Web 应用程序和 Web 服务器  
  
#### 配置 ASP.NET Web 应用程序和 Web 服务器  
  
1.  修改目标应用程序的 web.config 文件。  请参见[如何：修改 Web.Config 文件以检测和分析动态编译的 ASP.NET Web 应用程序](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md)。  
  
2.  在承载 Web 应用程序的计算机上打开命令提示符窗口。  
  
3.  初始化分析环境变量。  键入：  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     \- 或 \-  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** 启用内存分配数据的收集。  
  
    -   **\/globaltracegclife** 启用内存分配数据和对象生存期数据的收集。  
  
4.  重新启动计算机。  
  
## 运行分析会话  
  
#### 分析 ASP.NET Web 应用程序  
  
1.  启动探查器。  键入：  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   **\/start:trace** 选项初始化探查器。  
  
    -   **\/output:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:trace** 选项一起使用。  
  
    > [!NOTE]
    >  ASP.NET 应用程序通常需要 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|说明|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定拥有 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 工作进程的帐户的可选域名和用户名。  如果该进程以已登录用户之外的用户身份运行，则需要此选项。  Windows 任务管理器的“进程”选项卡上的“用户名”列中列出了名称。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他会话中的进程分析。  如果应用程序在其他会话中运行，则需要此选项。  会话 ID 列在 Windows 任务管理器的“进程”选项卡上的“会话 ID”列中。  **\/CS** 可指定为 **\/crosssession** 的缩略词。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|启动探查器，同时暂停数据收集。  使用 [\/globalon](../profiling/globalon-and-globaloff.md) 可继续分析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|从 `Config` 中所指定的处理器性能计数器收集信息。  计数器信息将添加到在每个分析事件中收集的数据中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
2.  通过典型方式启动 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 **VSPerfCmd.exe** 选项开始和停止向探查器数据文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   以下选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|说明|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|开始 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 线程 ID \(`TID`\) 所指定的线程的数据收集。|  
  
-   还可以使用 **VSPerfCmd.exe** [\/mark](../profiling/mark.md) 选项在数据文件中插入分析标记。  **\/mark** 命令添加一个标识符、一个时间戳和一个可选的用户定义的文本字符串。  标记可用于筛选探查器报告和数据视图中的数据。  
  
## 结束分析会话  
 若要结束分析会话，请关闭目标 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，停止 Internet Information Services \(IIS\) 以停止分析的进程，然后关闭探查器。  然后重新启动 IIS。  
  
#### 结束分析会话  
  
1.  关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  
  
2.  通过重置 Internet Information Services \(IIS\) 关闭 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 工作进程。  键入：  
  
     **IISReset \/stop**  
  
3.  关闭探查器。  键入：  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  重新启动 IIS。  键入：  
  
     **IISReset \/start**  
  
## 还原应用程序和计算机配置  
 完成所有分析后，替换 web.config 文件，清除分析环境变量，然后重新启动计算机以将服务器和 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序还原到其原始状态。  
  
#### 还原应用程序和计算机配置  
  
1.  将 web.config 文件替换为原始文件的副本。  
  
2.  （可选）。  清除分析环境变量。  键入：  
  
     **VSPerfCmd \/globaloff**  
  
3.  重新启动计算机。  
  
## 请参阅  
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)