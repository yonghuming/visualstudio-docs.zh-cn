---
title: "如何：使用命令行将独立本机应用程序与探查器一起启动以收集并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将独立本机应用程序与探查器一起启动以收集并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令行工具启动本机独立（客户端）应用程序以及收集进程和线程并发数据。  
  
 分析会话具有以下几部分：  
  
-   将应用程序与探查器一起启动  
  
-   控制数据收集  
  
-   结束分析会话  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要在命令提示符下使用探查器，必须将该工具路径添加到**“命令提示符”**窗口的 PATH 环境变量中，或添加到命令本身。  有关更多信息，请参见[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 随探查器一起启动应用程序  
 若要将目标应用程序与探查器一起启动，请使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md) **\/start** 和 **\/launch** 选项初始化探查器并启动应用程序。  还可以指定 **\/start** 和 **\/launch** 及其各自的选项。  还可以添加 **\/globaloff** 选项，以在目标应用程序启动时暂停数据收集。  然后，可以使用 **\/globalon** 开始收集数据。  
  
#### 将应用程序与探查器一起启动  
  
1.  在命令提示符下键入以下命令：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下表中的任意选项与 **\/start:concurrency** 选项一起使用。  
  
    |选项|说明|  
    |--------|--------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
2.  通过键入以下命令启动目标应用程序：  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     可以将下表中的任意选项与 **\/launch** 选项一起使用。  
  
    |选项|说明|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|指定一个字符串，该字符串包含要传递给目标应用程序的命令行参数。|  
    |[\/console](../profiling/console.md)|在单独的窗口中启动目标命令行应用程序。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|指定在应用程序加载了多个版本的公共语言运行时 \(CLR\) 时，要分析的 CLR 的版本。|  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 VSPerfCmd.exe 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   下表中的选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|说明|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始收集由进程 ID \(`PID`\) 或进程名称 \(*ProcName*\) 所指定的进程的数据。  **\/detach** 停止对指定进程的数据收集，如果未指定任何进程，则停止对所有进程的数据收集。|  
  
-   还可以使用 **VSPerfCmd.exe** [\/mark](../profiling/mark.md) 选项在数据文件中插入分析标记。  **\/mark** 命令添加一个标识符、一个时间戳和一个可选的用户定义的文本字符串。  标记可用于筛选探查器报告和数据视图中的数据。  
  
## 结束分析会话  
 探查器未在收集数据时，才能结束分析会话。  可以通过关闭分析的应用程序或调用 **VSPerfCmd \/detach** 选项来停止收集并发数据。  然后，可以调用 **VSPerfCmd \/shutdown** 选项关闭探查器并关闭分析数据文件。  
  
#### 结束分析会话  
  
1.  通过关闭探查器或在命令提示符下键入下面的命令，可将探查器从目标应用程序分离：  
  
     **VSPerfCmd \/detach**  
  
2.  通过在命令提示符下键入下面的命令关闭探查器：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)