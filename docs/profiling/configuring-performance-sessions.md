---
title: "为分析工具配置性能会话 | Microsoft Docs"
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
  - "常见任务, 性能"
  - "常见任务, 分析工具"
  - "分析工具, 常见任务"
  - "性能, 收集数据"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 为分析工具配置性能会话
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具，可以针对许多应用程序类型收集各种性能数据。  本节演示如何使用以及性能会话属性和目标二进制文件配置分析工具收集感兴趣的数据。  分析工具配置属性还可用于控制在分析运行中收集的数据量。  有关更多信息，请参见[控制数据收集](../profiling/controlling-data-collection.md)。  
  
> [!NOTE]
>  在许多情况下，使用“性能向导”的默认属性是一种收集分析数据的有效方法。  有关更多信息，请参见[性能分析初学者指南](../profiling/beginners-guide-to-performance-profiling.md)和[入门](../profiling/getting-started-with-performance-tools.md)。  
  
## 常规任务  
  
|任务|相关内容|  
|--------|----------|  
|**设置基本分析选项：**应将 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 配置为使用 Microsoft 符号服务器。  这样可确保您具有对当前 Windows 版本及其他 Microsoft 应用程序的函数和参数名等符号的访问权限。  还可以在启动分析会话之前指定其他常规选项，例如，对分析工具的系统权限和分析数据文件的名称。|-   [如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [如何：序列化符号信息](../profiling/how-to-serialize-symbol-information.md)<br />-   [如何：设置当前分析会话](../Topic/How%20to:%20Set%20the%20Current%20Session.md)<br />-   [如何：设置分析权限](../profiling/how-to-set-permissions.md)<br />-   [如何：设置分析数据文件名选项](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**指定要收集的数据：**用于配置分析会话的过程依赖于要分析的目标应用程序的类型和要收集的性能数据的类型。|-   [如何：选择收集方法](../profiling/how-to-choose-collection-methods.md)<br />-   [使用采样收集性能统计信息](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [收集 .NET 内存分配数据和生存期数据](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [如何：分析网页中的 JavaScript \(ECMA\) 代码](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [收集线程和进程并发数据](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [收集其他性能数据](../profiling/collecting-additional-performance-data.md)|  
|**设置高级配置选项：**当分析加载多个版本的公共语言运行时 \(CLR\) 的 .NET Framework 应用程序时，您可以指定要分析的版本。  当性能会话中存在多个 .exe 文件时，您可以设置二进制文件的启动顺序。|-   [如何：在并行方案中指定要分析的 .NET Framework 运行时](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)<br />-   [如何：指定要启动的二进制文件](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## 相关章节  
 [控制数据收集](../profiling/controlling-data-collection.md)  
  
## 请参阅  
 [使用分析工具](../profiling/performance-explorer.md)