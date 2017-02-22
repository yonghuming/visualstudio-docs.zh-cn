---
title: "分析工具问题疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 分析工具问题疑难解答
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您在使用分析工具时可能会遇到以下问题之一：  
  
-   [分析工具未收集任何数据](#NoDataCollected)  
  
-   [性能视图和报告将函数名称显示为数字](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> 分析工具未收集任何数据  
 在对应用程序进行分析后，分析数据 \(.vsp\) 文件未创建，您会在输出窗口或命令窗口中收到以下警告：  
  
 PRF0025: 未收集到任何数据。  
  
 该问题可由多个问题引起：  
  
-   使用采样或 .NET 内存方法分析的进程启动一个子进程，该子进程成为执行应用程序工作的进程。  例如，某些应用程序通过读取命令行来确定它们是作为 Windows 应用程序启动的还是作为命令行应用程序启动的。  如果请求了 Windows 应用程序，原始进程将启动一个配置为 Windows 应用程序的新进程，随后原始进程将退出。  由于分析工具不会自动收集子进程的数据，因此未收集任何数据。  
  
     在这种情况下若要收集分析数据，请将探查器附加到子进程而不要使用探查器启动应用程序。  有关更多信息，请参见[如何：在正在运行的进程中附加和分离探查器](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)和[附加 \(VSPerfCmd\)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> 性能视图和报告将函数名称显示为数字  
 在分析应用程序后，您在报告和视图中看到的是数字而不是函数名称。  
  
 造成此问题的原因是分析工具的分析引擎无法找到 .pdb 文件，而这些文件中包含将源代码信息（如函数名称和行号）映射到已编译文件的符号信息。  默认情况下，编译器会在应用程序文件生成时创建 .pdb 文件。  对 .pdb 文件本地目录的引用存储在已编译的应用程序中。  分析引擎会先在引用目录中查找 .pdb 文件，然后在当前包含应用程序文件的目录中查找。  如果找不到 .pdb 文件，分析引擎将使用函数偏移量而不是函数名称。  
  
 可通过以下两种方法之一来解决此问题：  
  
-   找到 .pdb 文件，然后将它们放入应用程序文件所在的目录。  
  
-   将符号信息嵌入分析数据 \(.vsp\) 文件。  有关更多信息，请参见[使用分析数据文件保存符号信息](../profiling/saving-symbol-information-with-performance-data-files.md)。  
  
> [!NOTE]
>  分析引擎要求 .pdb 文件与已编译的应用程序为同一版本。  来自应用程序文件的较早版本或稍后版本的 .pdb 文件将不起作用。