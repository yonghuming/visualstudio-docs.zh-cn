---
title: "收集 .NET 内存分配数据和生存期数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 内存分析方法"
  - "分析工具，.NET 内存方法"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 收集 .NET 内存分配数据和生存期数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具支持收集 .NET 内存分配数据和对象生存期数据，这些数据可帮助您检测应用程序中与内存相关的性能问题。  
  
-   有关 .NET 内存分配的数据包括所分配的 .NET Framework 内存对象的大小和数量。  
  
-   对象生存期数据包括在三代垃圾回收中回收的 .NET Framework 内存对象的大小和数量。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 可以使用采样或检测分析方法收集数据。  
  
-   使用采样方法时，探查器跟踪所有已启动或附加到的过程所生成的 .NET 内存分配和对象。  
  
-   使用检测方法时，探查器仅跟踪被检测模块所生成的那些 .NET 内存分配和对象。  
  
> [!IMPORTANT]
>  使用采样方法收集 .NET 内存数据（分配和\/或对象生存期）时，将忽略所有用户指定的采样事件，而使用相应的内存分配事件来收集数据。  
  
 如果允许分析 .NET 内存分配，则还要启用“分配”视图。  如果允许分析 .NET 生存期数据，则还要启用“对象生存期”视图。  有关更多信息，请参见[“分配”视图](../profiling/dotnet-memory-allocations-view.md)和[“对象生存期”视图](../profiling/object-lifetime-view.md)。  
  
 有关如何使用分析工具命令行工具收集 .NET 内存数据的信息，请参见[从命令行使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)中的“使用 .NET 内存方法收集内存分配数据和对象生存期数据”。  
  
### 收集 .NET 内存数据  
  
1.  在**“性能资源管理器”**中，右击性能会话，然后单击**“属性”**。  
  
2.  在*Performance Session***属性页**对话框上，单击“常规”选项卡，并且选择收集 .NET 对象分配信息”复选框。  
  
3.  若要收集 .NET 对象生存期数据，请选中**“还收集 .NET 对象的生存期信息”**复选框。  
  
## 常规任务  
 您可以在性能部分的*Performance Session* **属性页面**对话框中指定附加选项。  打开此对话框：  
  
-   在**“性能资源管理器”**中，右击性能会话名称，然后单击**“属性”**。  
  
 下表中的任务说明在收集 .NET 内存数据时，可以在*Performance Session* 属性页面对话框中指定的选项。  
  
|任务|相关内容|  
|--------|----------|  
|在**“常规”**页上，指定生成的分析数据 \(.vsp\) 文件的命名详细信息。|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [如何：设置分析数据文件名选项](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在**“启动”**页上，选择代码解决方案中有多个 .exe 项目时要启动的应用程序。|-   [收集层交互数据](../profiling/collecting-tier-interaction-data.md)|  
|在**“层交互”**页上，向分析运行添加 ADO.NET 调用数据。|-   [收集层交互数据](../profiling/collecting-tier-interaction-data.md)|  
|在**“Windows 事件”**页上，指定要随采样数据收集的一个或多个 Windows 事件跟踪 \(ETW\) 事件。|-   [如何：收集 Windows 事件跟踪 \(ETW\) 数据](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|在**“Windows 计数器”**页上，指定要作为标记添加到分析数据的一个或多个操作系统性能计数器。|-   [如何：收集 Windows 计数器数据](../profiling/how-to-collect-windows-counter-data.md)|  
|在**“高级”**页上，指定在应用程序模块使用多个 .NET Framework 运行时版本时，要分析的运行时版本。  默认情况下分析加载的第一个版本。|-   [如何：在并行方案中指定要分析的 .NET Framework 运行时](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|  
  
## 检测任务  
 下表中的任务是使用检测方法进行分析时专用的**“属性页”**对话框中的选项。  
  
|任务|相关内容|  
|--------|----------|  
|在**“二进制文件”**页上，指定检测的模块副本的位置。  默认情况下，原始二进制文件会移入备份文件夹。|-   [如何：重新指定检测后的二进制文件的位置](../profiling/how-to-relocate-instrumented-binaries.md)|  
|在**“检测”**页上，从分析中排除小型函数以减少分析开销，分析 ASP.NET 网页中的 JavaScript 代码，并指定在检测过程之前和之后要在命令提示符下运行的命令。|-   [如何：在检测中排除或包括短函数](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)<br />-   [如何：分析网页中的 JavaScript \(ECMA\) 代码](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [如何：指定检测前和检测后命令](../Topic/How%20to:%20Specify%20Pre-%20and%20Post-Instrument%20Commands.md)|  
|在**“CPU 计数器”**页上，指定要添加到分析数据的一个或多个处理器性能计数器。|-   [如何：收集 CPU 计数器数据](../profiling/how-to-collect-cpu-counter-data.md)|  
|在**“高级”**页上，指定所需的任何其他 VSInstr.exe 选项，如用于包含或排除特定函数的选项。  有关 VSInstr 选项的更多信息，请参见 [VSInstr](../profiling/vsinstr.md)|-   [如何：指定其他检测选项](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)<br />-   [如何：将检测限定为特定函数](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [如何：选择收集方法](../profiling/how-to-choose-collection-methods.md)   
 [性能会话属性](../profiling/performance-session-properties.md)