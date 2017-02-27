---
title: "“模块”视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.modules"
helpviewer_keywords: 
  - "“模块”视图"
  - "分析工具报告, “模块”视图"
  - "分析工具, “模块”视图"
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# “模块”视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“模块”视图列出分析数据的模块。  每个模块都是一个层次结构树的根节点。  模块的分析函数在模块节点下列出。  如果分析数据是使用采样方法收集的，则行信息在函数节点下列出，指令指针数据在行节点下列出。  
  
 展开或折叠模块名称可显示或关闭模块性能数据的视图。  
  
 若要添加或移除列，请在报告窗口中单击鼠标右键，然后选择**“添加\/移除列”**。  可以通过单击列名对数据进行排序。  有关更多信息，请参见 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)。  
  
 “模块”视图中有哪些列取决于用于收集数据的分析方法（采样或检测），以及在分析运行期间是否收集了 .NET 内存数据。  
  
## 请参阅  
 [“模块”视图](../profiling/modules-view-sampling-data.md)   
 [“模块”视图](../profiling/modules-view-instrumentation-data.md)   
 [“模块”视图 \- 检测](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [“模块”视图 \- 采样](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [“模块”视图](../profiling/modules-view-contention-data.md)