---
title: "“模块”视图 - 探查器争用数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“模块”视图"
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# “模块”视图 - 探查器争用数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

争用数据的“模块”视图显示由分析数据期间采样的模块所分组的并发数据。  每个模块都是一个层次结构树的根。  模块节点下列出从中发生争用事件的模块的函数。  
  
 如果在发生争用事件时函数正在执行其自己的代码，即函数位于调用堆栈的顶部，则在函数节点下列出正在执行的源行和指令地址。  由于在行或指令执行时收集源行或指令指针的数据，因此行数据和指令数据的非独占值和独占值始终相同。  
  
 下表说明争用数据的“模块”视图中各列的值。  
  
|列|说明|  
|-------|--------|  
|**独占阻塞的时间**|-   对于函数，为阻塞此函数执行函数体内代码的时间。  不包括该函数所调用的函数中的阻塞时间。<br />-   对于模块，为模块中各个函数独占阻塞时间之和。<br />-   对于行或指令，为阻塞此行或指令执行的时间。|  
|**独占阻塞的时间百分比**|-   对于函数或模块，为此函数或模块的独占阻塞时间占分析运行期间所有阻塞时间的百分比。<br />-   对于行或指令，为此行或指令执行阻塞的时间占分析运行期间所有阻塞时间的百分比。|  
|**独占争用**|-   对于函数，为此函数执行函数体内代码阻塞的次数。  不包括该函数所调用的函数中的争用。<br />-   对于模块，为模块中各个函数的独占争用之和。<br />-   对于行或指令，为阻塞此行或指令执行的次数。|  
|**独占争用数百分比**|-   对于函数或模块，为此函数或模块的独占争用占分析运行期间所有争用的百分比。<br />-   对于行或指令，为阻塞此行或指令执行的争用占分析运行期间所有争用的百分比。|  
|**非独占阻塞的时间**|-   对于函数，为阻塞此函数或此函数调用的函数执行的时间。<br />-   对于模块，为此模块中的至少一个函数位于堆栈上的阻塞时间之和。<br />-   对于行或指令，为阻塞此行或指令执行的时间。|  
|**非独占阻塞的时间百分比**|-   对于函数或模块，为此函数或模块的非独占阻塞时间占分析运行期间所有阻塞时间的百分比。<br />-   对于行或指令，为此行或指令执行的时间占分析运行期间所有阻塞时间的百分比。|  
|**非独占争用数**|-   对于函数，为阻塞此函数或此函数调用的函数执行的次数。<br />-   对于模块，为此模块中的至少一个函数位于堆栈上的争用的次数。<br />-   对于行或指令，为阻塞此行或指令执行的次数。|  
|**非独占争用数百分比**|-   对于函数或模块，为此函数或模块的非独占争用占分析运行期间所有争用的百分比。<br />-   对于行或指令，为此行或指令执行的时间占分析运行期间所有阻塞时间的百分比。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**模块名**|函数、行或指令指针所在模块的名称。|  
|**模块路径**|模块、函数、行或指令指针所在模块的路径。|  
|**名称**|模块或函数的名称。|  
|**进程 ID**|分析运行的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**源文件**|包含函数定义的源文件。|  
  
## 请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [“模块”视图](../profiling/modules-view.md)   
 [“模块”视图 \- 检测](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [“模块”视图 \- 采样](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [“模块”视图](../profiling/modules-view-instrumentation-data.md)   
 [“模块”视图](../profiling/modules-view-sampling-data.md)