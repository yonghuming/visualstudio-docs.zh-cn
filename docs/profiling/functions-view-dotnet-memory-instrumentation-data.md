---
title: "函数视图 - 探查器 .NET 内存检测数据 | Microsoft Docs"
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
  - "“函数”视图"
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 函数视图 - 探查器 .NET 内存检测数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用检测方法所收集的 .NET 内存分配分析数据有一个“函数”视图，其中列出在分析运行期间分配了内存的函数。  函数行报告内存分配的大小和数量，以及函数的计时数据。  
  
## 常规  
  
|列|说明|  
|-------|--------|  
|**函数名**|函数名。|  
|**函数地址**|函数的地址。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**调用数**|对此函数进行的调用总数。|  
|**源文件**|包含函数定义的源文件。|  
|**模块名**|函数所在模块的名称。|  
|**模块路径**|函数所在模块的路径。|  
|**进程 ID**|分析运行的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**时间独占探测系统开销**|此函数由检测导致的时间开销。  所有独占时间中已扣除探测开销。|  
|**时间包含探测系统开销**|此函数及其子函数由检测导致的时间开销。  所有非独占时间中已扣除探测开销。|  
  
## .NET 内存值  
 函数的非独占 .NET 内存值指由该函数及其子函数所创建的对象的数量（分配数）和大小（字节）。  
  
 独占内存值指由该函数而非其子函数所创建的对象的数量和大小。  
  
|列|说明|  
|-------|--------|  
|**非独占分配**|在此函数及此函数所调用的函数中所创建的对象总数。|  
|**非独占分配数 %**|在分析运行期间分配的，此函数的所有非独占分配对象数的百分比。|  
|**独占分配**|此函数在执行函数体内的代码时所创建的对象总数。  此数目不包括由此函数调用的函数所创建的对象。|  
|**独占分配数 %**|在分析运行期间创建的，此函数的所有独占分配对象数的百分比。|  
|**非独占字节数**|由此函数及此函数所调用的函数分配的内存字节数。|  
|**非独占字节数 %**|在分析运行期间分配的，此函数的所有非独占内存字节数的百分比。|  
|**独占字节数**|由此函数而非此函数所调用的函数分配的内存字节数。|  
|**独占字节数 %**|在分析运行期间分配的，此函数的所有独占内存字节数的百分比。|  
  
## 已用非独占时间值  
 已用非独占时间值是函数在调用堆栈上的时间。  该时间包括子函数所用的时间和调用操作系统（如上下文切换和输入\/输出操作）的时间。  
  
|列|说明|  
|-------|--------|  
|**已用包含时间**|对此函数的所有调用的总已用非独占时间。|  
|**已用非独占时间百分比**|此函数所用的已用非独占时间占分析运行中总已用非独占时间的百分比。|  
|**平均已用非独占时间**|对此函数的调用的平均已用非独占时间。|  
|**最长已用非独占时间**|对此函数的调用的最长已用非独占时间。|  
|**最短已用非独占时间**|对此函数的调用的最短已用非独占时间。|  
  
## 已用独占时间值  
 已用独占时间值是函数在调用堆栈顶部直接执行的时间。  该时间包括调用操作系统（如上下文切换和输入\/输出操作）的时间，但不包括子函数所用的时间。  
  
|列|说明|  
|-------|--------|  
|**已用独占时间**|对此函数的所有调用的总已用独占时间。|  
|**已用独占时间百分比**|此函数所用的总已用独占时间占分析运行中的总已用独占时间的百分比。|  
|**平均已用独占时间**|对此函数的调用的平均已用独占时间。|  
|**最长已用独占时间**|对此函数的调用的最长已用独占时间。|  
|**最短已用独占时间**|对此函数的调用的最短已用独占时间。|  
  
## 应用程序非独占时间值  
 应用程序非独占时间值是函数在调用堆栈上的时间。  该时间不包括调用操作系统（如上下文切换和输入\/输出操作）所用的时间，但包括子函数所用的时间。  
  
|列|说明|  
|-------|--------|  
|**应用程序包含时间**|对此函数的所有调用的总应用程序非独占时间。|  
|**应用程序非独占时间百分比**|此函数所用的总应用程序非独占时间占分析运行中的总已用非独占时间的百分比。|  
|**平均应用程序非独占时间**|对此函数的调用的平均应用程序非独占时间。|  
|**最长应用程序非独占时间**|对此函数的调用的最长应用程序非独占时间。|  
|**最短应用程序非独占时间**|对此函数的调用的最短应用程序非独占时间。|  
  
## 应用程序独占时间值  
 应用程序独占时间值是函数在调用堆栈顶部直接执行的时间。  该时间不包括调用操作系统（如上下文切换和输入\/输出操作）所用的时间，也不包括子函数所用的时间。  
  
|列|说明|  
|-------|--------|  
|**应用程序独占时间**|对此函数的所有调用的总应用程序独占时间。|  
|**应用程序独占时间百分比**|此函数所用的总应用程序独占时间占分析运行中的总已用独占时间的百分比。|  
|**平均应用程序独占时间**|对此函数的调用的平均应用程序独占时间。|  
|**最长应用程序独占时间**|对此函数的调用的最长应用程序独占时间。|  
|**最短应用程序独占时间**|对此函数的调用的最短应用程序独占时间。|  
  
## 请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [“函数”视图 \- 采样](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [“函数”视图](../profiling/functions-view-instrumentation-data.md)   
 [“函数”视图](../profiling/functions-view-sampling-data.md)