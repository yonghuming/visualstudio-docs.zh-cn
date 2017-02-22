---
title: "如何：使用命令行同时启用独立的 .NET Framework 应用程序和探查器，以收集并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行同时启用独立的 .NET Framework 应用程序和探查器，以收集并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的命令行工具启动 .NET Framework 独立（客户端）应用程序以及收集进程和线程并发数据  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，同时提供这些工具的 64 位和 32 位版本。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 在将探查器附加到应用程序时，可以暂停和继续数据收集。  若要结束分析会话，必须从应用程序分离探查器并显式关闭探查器。  
  
## 将应用程序与探查器一起启动  
 若要将 .NET Framework 目标应用程序与探查器一起启动，请使用 VSPerfClrEnv.exe 设置 .NET Framework 分析变量。  然后，使用 VSPerfCmd **\/start** 和 **\/launch** 选项初始化探查器并启动应用程序。  可以在单个命令行上指定 **\/start** 和 **\/launch** 及其各自的选项。  还可以向命令行添加 **\/globaloff** 选项，以便在目标应用程序启动时暂停数据收集。  然后，在一个单独的命令行上使用 **\/globalon** 开始收集数据。  
  
#### 将应用程序与探查器一起启动  
  
1.  打开命令提示符窗口。  
  
2.  启动探查器。  键入：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) 选项初始化探查器。  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|允许同时收集资源争用和线程执行数据。|  
        |**\/start:concurrency,resourceonly**|启用仅收集资源争用数据的操作。|  
        |**\/start:concurrency,threadonly**|启用仅收集线程执行数据的操作。|  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 选项对于 **\/start** 是必需的。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下列任意选项与 **\/start:concurrency** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|指定要允许其访问探查器的帐户的可选域名和用户名。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
3.  启动目标应用程序。  键入：  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     可以将以下任意选项与 **\/launch** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|指定一个字符串，该字符串包含要传递给目标应用程序的命令行参数。|  
    |[\/console](../profiling/console.md)|在单独的窗口中启动目标命令行应用程序。|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。|  
  
## 控制数据收集  
 在目标应用程序运行期间，通过使用 VSPerfCmd.exe 选项开始和停止向文件写入数据，可以控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
1.  以下 VSPerfCmd.exe 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始对由进程 ID \(`PID`\) 或进程名称 \(ProcName\) 指定的进程进行数据收集。  **\/detach** 停止对指定进程的数据收集，如果未指定具体进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 探查器未在收集数据时，才能结束分析会话。  可以通过关闭分析的应用程序或调用 **VSPerfCmd \/detach** 选项来停止收集并发数据。  然后，可以调用 **VSPerfCmd \/shutdown** 选项关闭探查器并关闭分析数据文件。  **VSPerfClrEnv \/off** 命令清除分析环境变量。  
  
#### 结束分析会话  
  
1.  执行以下操作之一从目标应用程序分离探查器。  
  
    -   关闭目标应用程序。  
  
         \- 或 \-  
  
    -   键入 **VSPerfCmd \/detach**  
  
2.  关闭探查器  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 请参阅  
 [收集并发数据](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)