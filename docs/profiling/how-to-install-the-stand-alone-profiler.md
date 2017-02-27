---
title: "如何：安装独立探查器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "性能工具, 安装独立探查器"
  - "分析工具, 独立探查器"
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：安装独立探查器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供了一个基于命令行的独立探查器，它可在没有安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 的情况下运行。  当计算机没有安装或无法安装开发环境时会发生这种情况。  例如，您不应该在成品 Web 服务器上安装开发环境。  
  
> [!NOTE]
>  使用独立探查器收集 ASP.NET 网站的性能数据时，建议使用 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 命令行工具，而不要使用 [VSPerfCmd](../profiling/vsperfcmd.md)。  
  
### 安装独立探查器  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安装媒体上包含 \\Standalone Profiler 路径的目录中，找到独立探查器安装程序 \(vs\_profiler.exe\)，然后运行该安装程序。  
  
2.  将 vsintr.exe 和 msdis150.dll 的路径添加到系统路径。  
  
    > [!NOTE]
    >  执行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的默认安装时，vsinstr.exe 和 msdis150.dll 位于 \\Program Files\\Visual Studio 10\\Team Tools\\Performance Tools 中。  
  
3.  在命令提示符处，键入 **VSInstr**。  
  
    > [!NOTE]
    >  如果显示了 vsinstr.exe 的用法信息，那么表明安装无误。  如果看见一条错误信息，该消息指出找不到 vsinstr.exe 或其一个依赖项，请确保您已经按步骤 2 中的说明正确设置了路径。  
  
4.  通过将 **\_NT\_SYMBOL\_PATH** 变量设置为 **symsrv\*symsrv.dll\*c:\\localcache\*http:\/\/msdl.microsoft.com\/download\/symbols** 来设置符号服务器  
  
5.  在使用系统环境变量设置了符号服务器后，请在新的命令提示处运行命令行探查器工具。  这将使新环境变量生效。  在命令提示符窗口中，键入以下命令：  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    >  有关如何设置符号服务器包的详细说明，请参见[如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)。  
  
6.  使用 [VSPerfReport](../profiling/vsperfreport.md) 工具将您的符号序列化到分析数据 \(.vsp\) 文件中。  使用 **VSPerfReport \/summary:all \/packsymbols** 开关。  如果数据文件中未插入符号，请确保设置了 \_NT\_SYMBOL\_PATH 环境变量。  
  
## 请参阅  
 [通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [演练：使用采样进行命令行分析](../Topic/Walkthrough:%20Command-Line%20Profiling%20Using%20Sampling.md)   
 [演练：使用检测进行命令行分析](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)