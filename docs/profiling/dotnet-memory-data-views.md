---
title: "分析工具 .NET 内存数据视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET 内存分析方法视图"
  - "分析工具, .NET 内存分析视图"
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 分析工具 .NET 内存数据视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节介绍有关包含 .NET 内存分析数据的探查器数据文件的视图和报告的参考信息。  
  
## 本节内容  
 [“摘要”视图](../profiling/summary-view-dotnet-memory-data.md)  
 列出分配了大多数内存的函数和类型。  
  
 [“分配”视图](../profiling/dotnet-memory-allocations-view.md)  
 列出分析运行期间分配的类型以及导致分配类型的调用树（执行路径）。  
  
 [“对象生存期”视图](../profiling/object-lifetime-view.md)  
 列出分析运行期间分配的类型、实例数、大小（以字节为单位）和类型的垃圾回收代。  
  
 [“调用关系树”视图 \- 采样](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 显示一个层次结构树，它表示分析运行期间各个函数的执行路径和内存分配数据。  
  
 [“模块”视图 \- 采样](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 按模块组织 .NET 内存分配数据，并列出分配内存时执行的函数、源代码行和指令。  
  
 [“调用方\/被调用方”视图 \- 采样](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 列出所选函数的内存分配数据，调用所选函数的函数以及所选函数调用的函数。  
  
 [“函数”视图 \- 采样](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 列出分析运行期间各个函数的内存分配数据。  
  
 [“行”视图 \- 采样](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 列出分析运行期间各个函数的源代码行的内存分配数据。  
  
 [“指令指针”\(IP\) 视图 \- 采样](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 列出分析运行期间各个函数的指令的内存分配数据。  
  
 [“调用关系树”视图 \- 检测](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 显示一个层次结构树，它表示分析运行期间被检测函数的执行路径、内存分配数据和详细计时数据。  
  
 [“模块”视图 \- 检测](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 按模块组织分析数据，并列出模块的函数、内存分配数据和详细计时信息。  
  
 [“调用方\/被调用方”视图 \- 检测](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 列出所选被检测函数的内存分配数据和详细计时信息，调用所选函数的函数以及所选函数调用的函数。  
  
 [“函数”视图 \- 检测](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 列出分析运行期间被检测函数的内存分配数据。  
  
## 参考  
 [函数详细信息视图](../profiling/function-details-view.md)  
 显示所选函数、调用该函数的函数以及该函数调用的函数之间的关系的图表。  
  
 [“进程”视图](../profiling/process-view.md)  
 列出进程和线程的开始和结束时间。  
  
 [“标记”视图](../profiling/marks-view.md)  
 列出插入到分析数据文件中的ETW和采样事件。  
  
## 相关章节  
 [采样方法数据视图](../profiling/profiler-sampling-method-data-views.md)  
 有关使用采样方法生成的探查器数据文件的视图和报告的参考信息。  
  
 [检测方法数据视图](../profiling/instrumentation-method-data-views.md)  
 使用检测方法生成的探查器数据文件的视图和报告的参考信息。