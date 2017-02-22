---
title: "使用 VSPerfASPNETCmd 进行快速网站分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用 VSPerfASPNETCmd 进行快速网站分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

利用 **VSPerfASPNETCmd** 命令行工具，可以轻松分析 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序。  与 [VSPerfCmd](../profiling/vsperfcmd.md) 命令行工具相比，选项有所减少，不必设置环境变量，并且不需要重新启动计算机。  通过独立探查器进行分析的首选方法是使用 **VSPerfASPNETCmd**。  有关详细信息，请参阅[如何：安装独立探查器](../profiling/how-to-install-the-stand-alone-profiler.md)。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 在某些情况下，如收集并发数据或暂停和继续进行分析，使用 **VSPerfCmd** 是首选的分析方法。  
  
> [!NOTE]
>  分析工具的命令行工具位于 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安装目录的 \\Team Tools\\Performance Tools 子目录中。  在 64 位计算机上，使用位于 32 位 \\Team Tools\\Performance Tools 目录中的 VSPerfASPNETCmd 工具。  若要使用探查器命令行工具，必须将该工具路径添加到命令提示符窗口的 PATH 环境变量或添加到命令本身。  有关详细信息，请参阅[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 分析 ASP.NET 应用程序  
 若要分析 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序，请键入以下部分描述的命令之一。  此时将启动网站，探查器开始收集数据。  执行应用程序然后关闭浏览器。  若要停止分析，请在命令提示符窗口中按 Enter 键。  
  
> [!NOTE]
>  默认情况下，命令提示符不在 **vsperfaspnetcmd** 命令之后返回。  可以使用 **\/nowait** 选项强制命令提示符返回。  参见[使用 /NoWait 选项](#UsingNoWait).  
  
## 使用采样方法收集应用程序统计信息  
 采样是 **VSPerfASPNETCmd** 工具的默认分析方法，因此不必在命令行上指定。  以下命令行从指定的 Web 应用程序收集应用程序统计信息：  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## 使用检测方法收集详细计时数据  
 使用以下命令行从动态编译的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 应用程序收集详细计时数据：  
  
 **vsperfaspnetcmd \/trace**  *websiteUrl*  
  
 如果要分析 Web 应用程序中静态编译的 .dll 文件，必须使用 [VSInstr](../profiling/vsinstr.md) 命令行工具检测这些文件。  vsperfaspnetcmd \/trace 命令将包括已检测文件中的数据。  
  
## 收集 .NET 内存数据  
 **\/Memory** 选项收集有关 .NET 内存中对象分配的数据，还可以收集有关这些对象的生存期的数据。  分配数据收集是 **\/Memory** 数据选项的默认模式，因此不必在命令行上指定。  
  
 **vsperfaspnetcmd \/memory** *websiteUrl*  
  
 使用 **Lifetime** 参数可以收集对象生存期数据和分配数据：  
  
 **vsperfaspnetcmd \/memory:lifetime** *websiteUrl*  
  
 还可以使用 **\/Trace** 选项随 .NET 内存数据收集详细计时信息：  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/trace** `websiteUrl`  
  
## 收集层交互数据  
  
> [!WARNING]
>  可以使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], or [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] 收集层交互分析\(TIP\)数据.  然而层交互分析数据只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 和 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中查看。  
>   
>  若要在 Windows 8 上使用数据提示或 Windows Server 2012，必须使用检测 \(**\/trace**\) 选项。  
  
 随采样数据收集层交互数据：  
  
 **vsperfaspnetcmd \/tip** `websiteUrl`  
  
 随检测数据收集层交互数据：  
  
 **vsperfaspnetcmd \/trace \/tip** *websiteUrl*  
  
 随 .NET 内存数据收集层交互数据：  
  
 **vsperfaspnetcmd \/memory**\[**:lifetime**\] **\/tip** *websiteUrl*  
  
##  <a name="UsingNoWait"></a> 使用 \/NoWait 选项  
 默认情况下，命令提示符不在 **vsperfaspnetcmd** 命令之后返回。  可以使用以下语法选项强制命令提示符返回。  随后可以在命令提示符窗口中执行其他操作。  若要结束分析，请在单独的 **vsperfaspnetcmd** 命令中使用 **\/shutdown** 选项。  
  
 开始分析：  
  
 **vsperfaspnetcmd** \[*\/Options*\] **\/nowait** *websiteUrl*  
  
 结束分析：  
  
 **vsperfaspnetcmd \/shutdown** *websiteUrl*  
  
## 附加选项  
 可将以下任一选项添加到本节前面列出的命令中，**vsperfaspnetcmd \/shutdown** 命令除外。  
  
|选项|说明|  
|--------|--------|  
|**\/Output:** `VspFile`|默认情况下，分析数据 \(.vsp\) 文件在当前目录下创建，其文件名为 **PerformanceReport.vsp**。  使用 \/output 选项可以指定不同的位置和\/或文件名。|  
|**\/PackSymbols:Off**|默认情况下，VsPerfASPNETCmd 将符号（函数和参数名等）嵌入到 .vsp 文件中。  如果嵌入符号，则分析数据文件可能变得很大。  如果在分析数据时将具有对包含符号的 .pdb 文件的访问权限，则使用 \/packsymbols:off 选项可以禁止嵌入符号。|