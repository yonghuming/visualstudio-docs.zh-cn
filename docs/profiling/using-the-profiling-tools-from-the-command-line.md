---
title: "从命令行使用分析工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令行, 性能工具"
  - "命令行工具，性能工具"
  - "分析工具，命令行"
  - "工具，命令行"
  - "命令行, 工具"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 从命令行使用分析工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的命令行工具，可以在命令提示符下分析应用程序，并且可以通过使用批处理文件和脚本进行自动分析。  还可以在命令提示符下生成报告文件。  可以使用轻量独立探查器来收集未安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的计算机上的数据。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**设置符号位置：**若要显示函数和参数的名称，探查器必须对所分析的二进制文件的符号 \(.pdb\) 文件具有访问权限。  这些文件应包括 Microsoft 操作系统和您要在分析中查看的应用程序的符号文件。  可以使用公共 Microsoft 符号服务器来确保所具有的 Microsoft 二进制文件的 .pdb 文件是正确的。|-   [如何：从命令行指定符号文件位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**分析应用程序：**用于分析目标应用程序的命令行工具和选项取决于应用程序的类型、分析方法以及目标是托管应用程序还是本机应用程序。|-   [从命令行使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [分析服务](../profiling/command-line-profiling-of-services.md)|  
|**创建 .xml 和 .csv 报告：**可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的界面中查看在命令提示符下进行分析时创建的数据文件。  还可以使用 VSPerfReport 命令行工具生成数据的 .xml 或逗号分隔值 \(.csv\) 文件。|-   [从命令行创建探查器报告](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**在未安装 Visual Studio 的计算机上分析代码：**可以使用分析工具独立探查器来收集未安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的计算机上的应用程序的数据。|-   [如何：安装独立探查器](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## 引用  
 [命令行分析工具参考](../profiling/command-line-profiling-tools-reference.md)  
  
## 请参阅  
 [使用分析工具](../profiling/performance-explorer.md)