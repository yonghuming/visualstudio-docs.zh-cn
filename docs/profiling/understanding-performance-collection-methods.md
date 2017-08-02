---
title: "了解分析方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.methodpage"
helpviewer_keywords: 
  - "分析工具，分析方法"
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 了解分析方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 分析工具提供五种可用于收集性能数据的方法。  本主题介绍不同的方法，并提出了一些情况，在这些情况下使用某一特定方法收集数据可能比较合适。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
|方法|描述|  
|--------|--------|  
|[采样](#sampling)|收集有关由应用程序执行的工作的数据。|  
|[检测](#instrumentation)|收集有关每个函数调用的详细计时信息。|  
|[并发](#concurrency)|收集有关多线程应用程序的详细信息。|  
|[.NET 内存](#net_memory)|收集有关 .NET 内存分配和垃圾回收的详细信息。|  
|[层交互](#tier_interaction)|收集有关对 SqlServer 数据库的同步 ADO.NET 函数调用的信息。<br /><br /> 可使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], or [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)] 收集层交互分析.  然而层交互数据只能在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] or [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 中查看。|  
  
 借助某些分析方法，您还可以收集附加的数据，如软件和硬件性能计数器。  有关详细信息，请参阅[收集其他性能数据](../profiling/collecting-additional-performance-data.md)。  
  
##  <a name="sampling"></a> 采样  
 采样分析方法收集分析运行期间应用程序所执行工作的相关统计数据。  采样方法是轻量的，对应用程序方法的执行产生的影响非常小。  
  
 采样是 Visual Studio 中分析工具的默认方法。  此方法对于以下情况十分有用：  
  
-   应用程序性能的初步研究。  
  
-   调查涉及处理器 \(CPU\) 使用率的性能问题。  
  
 采样分析方法按设置的时间间隔中断计算机处理器并收集函数调用堆栈。  对于正在执行的函数，将累加独占样本计数；对于调用堆栈上的所有调用函数，将累加非独占计数。  采样报告将显示已分析模块、函数、源代码行和指令的这两项计数的总和。  
  
 默认情况下，探查器将采样间隔设置为 CPU 周期。  可以将间隔类型更改为其他 CPU 性能计数器，并可以为间隔设置计数器事件数。  还可以收集层交互分析 \(TIP\) 数据，该数据提供通过 ADO.NET 对 SQL Server 数据库执行的查询的相关信息。  
  
 [使用采样收集性能统计信息](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
 [了解采样数据值](../profiling/understanding-sampling-data-values.md)  
  
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> 检测  
 检测分析方法将收集已分析应用程序中函数调用的详细计时信息。  检测分析对于以下情况十分有用：  
  
-   调查输入\/输出瓶颈，如磁盘 I\/O。  
  
-   特定模块或函数集的详细检查。  
  
 检测方法将向二进制文件中注入代码，用于捕获已检测文件中的每个函数以及这些函数执行的每个函数调用的相关计时信息。  检测方法还将确定何时将函数调入操作（如写入文件）的运行阶段。  检测报告用四个值来表示函数或源代码行占用的总时间：  
  
-   已用非独占时间 － 执行该函数或源行所用的总时间。  
  
-   应用程序非独占时间 － 执行该函数或源行所用的时间，但不包括对操作系统的调用所用的时间。  
  
-   已用独占时间 － 执行该函数体或源代码行体中的代码所用的时间。  不包括执行该函数或源行调用的函数所用的时间。  
  
-   应用程序独占时间 － 执行该函数体或源代码行体中的代码所用的时间。  不包括执行对操作系统的调用所用的时间以及执行该函数或源行调用的函数所用的时间。  
  
 还可以使用检测方法收集 CPU 和软件性能计数器。  
  
 [了解检测数据值](../profiling/understanding-instrumentation-data-values.md)  
  
 [使用检测收集详细计时数据](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> 并发  
 并发分析收集有关多线程应用程序的信息。  资源争用分析收集每次争用线程被强制等待访问共享资源时的详细调用堆栈信息。  并发可视化还收集有关以下方面的更多常规信息：多线程应用程序如何与自身、硬件、操作系统和主机计算机上的其他进程进行交互：  
  
-   资源争用报告将显示争用的总次数，以及发生等待的模块、函数、源代码行和指令等待资源所用的总时间。  时间线图也会在发生争用时显示争用。  
  
-   并发可视化工具将显示图形信息，用于查找性能瓶颈、CPU 利用率不足、线程争用、线程迁移、同步延迟、I\/O 重叠区域和其他信息。  如果可能，图形输出将链接到调用堆栈和源代码数据。  只能收集命令行和 Windows 应用程序的并发可视化数据。  
  
 [了解资源争用数据值](../profiling/understanding-resource-contention-data-values.md)  
  
 [收集线程和进程并发数据](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
 [资源争用数据视图](../profiling/resource-contention-data-views.md)  
  
 [并发可视化工具](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> .NET 内存  
 .NET 内存分配分析方法在被分析的应用程序中每次分配 .NET Framework 对象时都中断计算机处理器。  同时收集对象生存期数据时，探查器会在每次 .NET Framework 垃圾回收后中断处理器。  
  
 探查器将收集有关分配中所创建或垃圾回收中所销毁的对象的类型、大小和数量的信息。  
  
-   发生分配事件时，探查器将收集有关函数调用堆栈的附加信息。  对于当前正在执行的函数，将累加独占分配计数；对于调用堆栈上的所有调用函数，将累加非独占计数。.NET 报告将显示已分析类型、模块、函数、源代码行和指令的这两项计数的总和。  
  
-   发生垃圾回收时，探查器将收集所销毁对象的相关数据，以及每代垃圾回收中对象的相关信息。  在分析运行结束时，探查器将记录未显式销毁的对象的相关数据。  对象生存期报告将显示在分析运行中分配的每种类型的总计。  
  
 .NET 内存分析可用于采样或检测模式。  所选模式不会影响 .NET 内存分析所特有的分配报告和对象生存期报告：  
  
-   在采样模式下运行 .NET 内存分析时，profiler.NET 将内存分配事件作为时间间隔，并显示所分配对象的数量以及作为报告中的非独占值和独占值分配的总字节数。  
  
-   在检测模式下运行 .NET 内存分析时，将随非独占分配值和独占分配值一起收集详细计时信息。  
  
 [了解内存分配数据值和对象生存期数据值](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
 [收集 .NET 内存分配数据和生存期数据](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [.NET 内存数据视图](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> 层交互  
 层交互分析向分析数据文件中添加有关 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 页（或其他应用程序）与 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 数据库之间的同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 调用的信息。  数据包括调用的次数和时间，以及最长时间和最短时间。  可将层交互数据添加到使用采样、检测、.NET 内存或并发方法收集的分析数据中。  
  
 ![层交互分析数据](~/profiling/media/tierinteraction_profilingtools.png "TierInteraction\_ProfilingTools")  
通过分析工具收集的层交互数据  
  
 [收集层交互数据](../profiling/collecting-tier-interaction-data.md)  
  
 [层交互视图](../profiling/tier-interaction-views.md)  
  
## 请参阅  
 [如何：为 Web 站点收集性能数据](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [性能分析初学者指南](../profiling/beginners-guide-to-performance-profiling.md)