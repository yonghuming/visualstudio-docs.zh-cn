---
title: "使用采样收集性能统计信息 | Microsoft Docs"
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
  - "分析工具, 采样"
  - "采样分析方法"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 使用采样收集性能统计信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，[!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]分析工具采样方法每 10,000,000 个处理器周期（在频率为 1 GHz 的计算机上这一时间大约为每百分之一秒）收集一次分析信息。  采样方法对于查找处理器利用率问题很有用，并且大多数性能调查都建议以此方法开始。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 可以使用以下过程之一指定采样方法：  
  
-   在分析向导的第一页上，单击**“CPU 采样\(建议\)”**。  
  
-   在**“性能资源管理器”**工具栏上的**“方法”**列表中，单击**“采样”**。  
  
-   在性能会话的属性对话框的**“常规”**页上，单击**“采样”**。  
  
## 常规任务  
 您可以在性能部分的*Performance Session* **属性页面**对话框中指定附加选项。  打开此对话框：  
  
-   在**“性能资源管理器”**中，右击性能会话名称，然后单击**“属性”**。  
  
 下表中的任务介绍在使用采样方法进行分析时，可以在*Performance Session* 属性页 对话框中指定的各个选项。  
  
|任务|相关内容|  
|--------|----------|  
|在**“常规”**页上，添加 .NET 内存分配和生存期数据收集，并为生成的分析数据 \(.vsp\) 文件指定命名详细信息。|-   [收集 .NET 内存分配数据和生存期数据](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [如何：设置分析数据文件名选项](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在**“采样”**页上，更改采样率和\/或将采样事件从处理器时钟周期更改为另一个处理器性能计数器。|-   [如何：选择采样事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)|  
|在**“启动”**页上，如果代码解决方案中有多个 .exe 项目，则指定要启动的应用程序及启动顺序。|-   [收集层交互数据](../profiling/collecting-tier-interaction-data.md)|  
|在**“层交互”**页上，将 ADO.NET 调用信息添加到分析运行期间收集的数据。|-   [收集层交互数据](../profiling/collecting-tier-interaction-data.md)|  
|在**“Windows 事件”**页上，指定要随采样数据收集的一个或多个 Windows 事件跟踪 \(ETW\) 事件。|-   [如何：收集 Windows 事件跟踪 \(ETW\) 数据](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|在**“Windows 计数器”**页上，指定要作为标记添加到分析数据的一个或多个操作系统性能计数器。|-   [如何：收集 Windows 计数器数据](../profiling/how-to-collect-windows-counter-data.md)|  
|在**“高级”**页上，指定在应用程序模块使用多个 .NET Framework 运行时版本时，要分析的运行时版本。  默认情况下分析加载的第一个版本。|-   [如何：在并行方案中指定要分析的 .NET Framework 运行时](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|