---
title: "如何：使用命令行将探查器附加到 ASP.NET Web 应用程序中以收集并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令行将探查器附加到 ASP.NET Web 应用程序中以收集并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主题介绍如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的命令行工具将探查器附加到 ASP.NET 应用程序中，并收集进程和线程并发数据。  
  
 分析工具的命令行工具位于 Visual Studio 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，64 位和 32 位版本的工具都可用。  若要在命令提示符下使用探查器，必须将该工具路径添加到**“命令提示符”**窗口的 PATH 环境变量中，或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要收集并发数据，请将探查器附加到承载网站的 ASP.NET 辅助进程。  在将探查器附加到应用程序时，可以暂停和继续数据收集。  若要结束分析会话，不得再将探查器附加到应用程序，并且必须显式关闭探查器。  在大多数情况下，应在会话结束时清除分析环境变量。  
  
## 附加探查器  
  
#### 将探查器附加到 ASP.NET 应用程序  
  
1.  通过键入以下命令启动探查器：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) 选项对探查器进行初始化以收集资源争用数据。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile`  选项必须与 **\/start** 一起使用。  `OutputFile` 指定分析数据 \(.vsp\) 文件的名称和位置。  
  
     可以将下表中的任意选项与 **\/start** 选项一起使用。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|指定要允许其访问探查器的帐户的可选域名和用户名。|  
    |[\/crosssession](../profiling/crosssession.md)|启用其他登录会话中的进程分析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定要在分析过程中收集的 Windows 性能计数器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|仅与 **\/wincounter** 一起使用。  指定 Windows 性能计数器收集事件之间间隔的毫秒数。  默认值为 500。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定要在分析过程中收集的 Windows 事件跟踪 \(ETW\) 事件。  将在单独的 \(.etl\) 文件中收集 ETW 事件。|  
  
2.  通过典型方式启动 ASP.NET 应用程序。  
  
3.  通过键入以下命令将探查器附加到 ASP.NET 辅助进程：**VSPerfCmd \/attach:**`PID` \[**\/targetclr:**`Version`\]  
  
    -   `PID` 指定 ASP.NET 辅助进程的 ID 或名称。  可以在 Windows 任务管理器中查看所有正在运行的进程的进程 ID。  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` 指定在应用程序中加载了多个版本的公共语言运行时 \(CLR\) 时要分析的运行时的版本。  此参数是可选的。  
  
## 控制数据收集  
 在应用程序运行期间，可以使用 VSPerfCmd.exe 选项开始和停止向文件写入数据，从而控制数据收集。  通过控制数据收集，可以收集程序执行的特定阶段（如启动或关闭应用程序）的数据。  
  
#### 开始和停止数据收集  
  
-   下表中的 VSPerfCmd 选项对可开始和停止数据收集。  在单独的命令行上指定每个选项。  您可以多次打开和关闭数据收集。  
  
    |选项|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|开始 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有进程的数据收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|开始 \(**\/processon**\) 或停止 \(**\/processoff**\) 进程 ID \(`PID`\) 所指定的进程的数据收集。|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** 开始收集由进程 ID \(`PID`\) 或进程名称 \(*ProcName*\) 所指定的进程的数据。  **\/detach** 停止对指定进程的数据收集，如果未指定任何进程，则停止对所有进程的数据收集。|  
  
## 结束分析会话  
 探查器未在收集数据时，才能结束分析会话。  通过重新启动 ASP.NET 辅助进程或调用 **VSPerfCmd \/detach** 选项，可以停止从用并发方法进行分析的应用程序中收集数据。  然后，可以调用 **VSPerfCmd \/shutdown** 选项关闭探查器并关闭分析数据文件。  **VSPerfClrEnv \/globaloff** 命令清除分析环境变量，但只有重新启动计算机之后才会重置系统配置。  
  
#### 结束分析会话  
  
1.  通过关闭探查器或在命令提示符下键入下面的命令，可从目标应用程序中分离探查器：  
  
     **VSPerfCmd \/detach**  
  
2.  通过在命令提示符下键入下面的命令关闭探查器：  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 请参阅  
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [使用 VSPerfASPNETCmd 进行快速网站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)