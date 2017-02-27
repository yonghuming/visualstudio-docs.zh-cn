---
title: "“调用方/被调用方”视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "分析工具, 报告, “调用方/被调用方”视图"
  - "分析工具, “调用方/被调用方”视图"
  - "性能报告, “调用方/被调用方”视图"
  - "“调用方/被调用方”视图"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# “调用方/被调用方”视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“调用方\/被调用方”视图显示有关所选函数及其父函数和子函数的分析信息。  “调用方\/被调用方”视图包含三个网格：  
  
 **“当前函数”**显示在中间网格内，用于显示有关所选函数的分析信息。  值包括在分析运行期间收集的对该函数的所有调用。  
  
 **“调用当前函数的函数”**显示在顶部网格内，用于显示因调用方（父）函数的调用，而生成的所选（当前）函数的值的数量。  
  
 **“由当前函数调用的函数”**显示在底部网格内，用于显示在当前函数调用被调用方（子）函数时，所选函数的子函数的相关分析信息。  
  
 “调用方\/被调用方”视图中会显示哪些列，这取决于在分析运行期间，收集数据时使用的分析方法（采样还是检测），以及是否收集了 .NET 内存数据。  
  
 通过双击“报告”视图上下两部分列出的任何一种函数，可以选择将该函数作为视图中间部分的“当前函数”。  “报告”视图会自动更新，以反映所做的更改。  
  
 您可以通过单击列名对数据进行排序。  可以向“调用方\/被调用方”视图添加其他列。  有关更多信息，请参见 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)。  
  
## 请参阅  
 [调用方\/被调用方视图](../profiling/caller-callee-view-sampling-data.md)   
 [“调用方\/被调用方”视图](../profiling/caller-callee-view-instrumentation-data.md)   
 [“调用方\/被调用方”视图 \- 检测](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [“调用方\/被调用方”视图 \- 采样](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [“调用方\/被调用方”视图](../profiling/caller-callee-view-contention-data.md)