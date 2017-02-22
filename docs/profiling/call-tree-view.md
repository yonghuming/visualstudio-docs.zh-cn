---
title: "“调用关系树”视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "“调用关系树”视图"
  - "性能报告, “调用关系树”视图"
  - "分析工具报告, “调用关系树”视图"
  - "分析工具, “调用关系树”视图"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “调用关系树”视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“调用关系树”视图显示遍历所分析的应用程序的函数执行路径。  关系树的根是应用程序或组件的入口点。  每个函数节点都列出它调用的所有函数以及有关这些函数调用的性能数据。  
  
 “调用关系树”视图还可以展开和突出显示消耗时间最多或采样频率最高的函数的执行路径。  若要显示最损性能的路径，请右击该函数，然后单击**“展开热路径”**。  
  
 分析运行中的每个进程都显示为根节点。  您可以通过右击要设置为开始节点的节点，然后选择**“设置根”**来设置“调用关系树”视图的开始节点。  
  
 设置根节点后，将消除视图中除所选节点的子树之外的所有其他项。  您可以将根节点重新设置为查看的节点。  在“调用关系树”视图窗口中，右击并选择**“重新设置根”**。  
  
 可以自定义“调用关系树”视图来添加或移除列。  右击**“列名称标题栏”**，然后选择**“添加\/移除列”**。  
  
 通过限制显示的数据量，可配置“调用关系树”视图进行降噪。  使用降噪后，性能问题在视图中就变得较为突出。  当性能问题易于区分时，分析就变得较为轻松了。  有关更多信息，请参见 [如何：在报告视图中配置降噪](../profiling/how-to-configure-noise-reduction-in-report-views.md)。  
  
> [!NOTE]
>  如果将降噪配置为在启用时显示警告，那么将在报告中显示信息栏。  
  
 有关“调用关系树”视图中的列定义的更多信息，请参见以下内容：  
  
 [“调用关系树”视图](../profiling/call-tree-view-sampling-data.md)  
  
 [“调用关系树”视图](../profiling/call-tree-view-instrumentation-data.md)  
  
 [“调用关系树”视图 \- 采样](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [“调用关系树”视图](../profiling/call-tree-view-contention-data.md)  
  
## 请参阅  
 [分析工具报告视图](../profiling/performance-report-views.md)   
 [了解检测数据值](../profiling/understanding-instrumentation-data-values.md)   
 [了解采样数据值](../profiling/understanding-sampling-data-values.md)