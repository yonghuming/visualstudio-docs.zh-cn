---
title: "“摘要”视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "性能报告, “摘要”视图"
  - "分析工具报告, “摘要”视图"
  - "分析工具, “摘要”视图"
  - "“摘要”视图"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# “摘要”视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“摘要”视图显示有关分析运行期间，最占系统资源的函数或对象的信息。  此视图根据分析方法的性能指标，提供一个时间线图，以及最占系统资源的函数或对象的两个或多个列表。  该视图中的数据取决于所用的分析方法（采样、检测或并发）以及是否收集 .NET 内存分配。  
  
 对于除并发数据的“摘要”视图以外的所有“摘要”视图，“摘要”视图中的时间线图显示被分析的应用程序在进行分析的这段时间内的处理器 \(CPU\) 使用率。  
  
-   如果在图表上指定一个时间段，则您可以重新分析该段的数据或将时间线显示缩放到指定的时间段。  有关更多信息，请参见[如何：从摘要时间线中筛选报告视图](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)  
  
-   可以在“摘要”视图列表中单击函数打开函数的“函数详细信息”视图。  还可以右击其他视图选项的函数。  
  
-   若要修改在“摘要”视图列表中显示的项目数量，请打开**“工具”**菜单，指向**“选项”**，然后单击**“性能工具”**。  在**“常规设置”**下，修改**“‘摘要’视图中的函数数目”**设置。  
  
## 通知链接  
 可以单击通知列表中的链接为报表设置显示选项。  列表在时间线图表的右侧。  
  
|||  
|-|-|  
|**显示非用户代码**<br /><br /> **显示仅我的代码**|不可用于本机代码或分析数据，该数据通过使用检测方法收集。  在仅显示用户代码中的数据（**“仅显示我的代码”**）与显示包括系统代码在内的所有代码中的数据（**“显示非用户代码”**）之间切换。  默认情况下，数据仅限于用户代码。  要更改设置，请参见[如何：筛选报告视图以显示“仅我的代码”](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md)。|  
|**查看指南**|在**“错误列表”**窗口中显示性能规则警告。  有关更多信息，请参见[使用性能规则对数据进行分析](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## 报告  
 可以单击报表列表中的链接，打开不同的视图并比较、保存或筛选报表。  列表在时间线图表的右侧。  
  
|||  
|-|-|  
|**显示剪裁的调用树**|在“调用树”视图中，显示最占系统资源的执行路径。  有关更多信息，请参见 [“调用关系树”视图](../profiling/call-tree-view.md)。|  
|**显示热线**|不适用于使用检测方法收集的分析数据。  在“线条”视图中，显示最占系统资源的源代码行。  有关更多信息，请参见 [“行”视图](../profiling/lines-view.md)。|  
|**比较报告**|显示可以指定要与当前文件进行比较的另一个分析数据文件的**“选择要比较的分析文件”**对话框。  有关更多信息，请参见 [比较分析工具数据文件](../profiling/comparing-performance-data-files.md)。|  
|**导出报告数据**|显示可以指定一个或多个要保存为逗号分隔值 \(.csv\) 文件或 .xml 文件的报表视图的**“导出报告”**对话框。  有关更多信息，请参见 [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/zh-cn/174b5bd3-df9b-4fd4-88d4-76032ab90451)。|  
|**保存分析的报告**|将当前的分析数据文件保存为 .vsps 文件，该文件在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 界面可更快速地打开。  有关更多信息，请参见 [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/zh-cn/0340ddde-caf4-48ac-8af3-d15dcdade556)。|  
|**筛选报告数据**|显示可以在其中指定条件来限制报表视图中的数据的分析报表筛选器窗格。  有关更多信息，请参见[分析工具报告视图筛选器](../profiling/performance-report-view-filter.md)|  
|**切换全屏显示**|切换报表视图的全屏模式。|  
  
## 请参阅  
 [“摘要”视图](../profiling/summary-view-sampling-data.md)   
 [“摘要”视图](../profiling/summary-view-instrumentation-data.md)   
 [“摘要”视图](../profiling/summary-view-dotnet-memory-data.md)