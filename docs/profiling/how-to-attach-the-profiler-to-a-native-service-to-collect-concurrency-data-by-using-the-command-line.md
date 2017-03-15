---
title: "如何：使用命令行将探查器附加到本机服务以收集并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到本机服务以收集并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的命令行工具将探查器附加到本机 \(C\/C\+\+\) 服务以及使用采样方法收集进程和线程并发数据。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  分析工具的命令行工具位于 Visual Studio 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要在命令提示符下使用探查器，必须将工具路径添加到**“命令提示符”**窗口的 PATH 环境变量中，或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 在将探查器附加到服务时，可以暂停和继续数据收集。  若要结束分析会话，不得再将探查器附加到服务，并且必须显式关闭探查器。  
  
## 附加探查器  
 若要将探查器附加到本机服务，可以使用 **VSPerfCmd** 的 **\/start** 和 **\/attach** 选项初始化探查器，并将其附加到目标应用程序。  可以在单个命令行上指定 **\/start** 和 **\/attach** 及其各自的选项。  还可以添加 **\/globaloff** 选项，以在目标应用程序启动时暂停数据收集。  然后，可以使用 **\/globalon** 开始收集数据。  
  
#### 将探查器附加到本机服务  
  
1.  如果该服务未运行，则启动该服务。  
  
2.  通过在命令提示符下键入以下命令启动探查器：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下表中的任意选项与 **\/start** 选项一起使用。  
  
    > [!NOTE]
    >  大多数服务都要求使用 **\/user** 和 **\/crosssession** 选项。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|指定要允许其访问探查器的帐户的可选域名和用户名。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
3.  通过在命令提示符下键入以下命令，将探查器附加到服务：  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` 指定目标应用程序的进程 ID 或进程名称。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 VSPerfCmd.exe 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   下表中的选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始收集由进程 ID \(`PID`\) 或进程名称 \(*ProcName*\) 所指定的进程的数据。  **\/detach** 停止对指定进程的数据收集，如果未指定任何进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 探查器未在收集数据时，才能结束分析会话。  通过停止服务，或调用 **VSPerfCmd \/detach** 选项，可以停止从正在用并发方法分析的本机服务中收集数据。  然后，可以调用 **VSPerfCmd \/shutdown** 选项关闭探查器并关闭分析数据文件。  
  
#### 结束分析会话  
  
1.  通过停止服务或在命令提示符下键入以下命令，将探查器与目标应用程序分离：  
  
     键入 **VSPerfCmd \/detach**  
  
2.  通过在命令提示符下键入下面的命令关闭探查器：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)