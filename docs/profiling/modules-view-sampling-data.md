---
title: "“模块”视图 - 探查器采样数据 | Microsoft Docs"
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
  - "“模块”视图"
  - "采样分析方法, “模块”视图"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “模块”视图 - 探查器采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

采样数据的“模块”视图显示由分析数据期间采样的模块所分组的性能数据。  每个模块都是一个层次结构树的根。  模块节点下列出模块的被采样函数。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 如果在收集样本时执行函数（即函数位于调用堆栈的顶部），则在函数节点下列出正在执行的源行和指令地址。  由于在行或指令执行时收集源行或指令指针的数据，因此行数据和指令数据的非独占值和独占值始终相同。  
  
|列|描述|  
|-------|--------|  
|**名称**|模块、函数、行号或指令指针地址的名称。|  
|**进程 ID**|分析运行的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**模块名**|函数、行或指令指针所在模块的名称。|  
|**模块路径**|模块、函数、行或指令指针所在模块的路径。|  
|**源文件**|包含函数定义的源文件。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**非独占样本数**|-   对于函数，为从中执行此函数或此函数所调用函数的样本的数量；即包含此函数的调用堆栈样本的数量。<br />-   对于模块，为从中至少执行模块中一个函数的样本的数量。<br />-   对于行或指令，为从中执行此行或指令的样本的数量。|  
|**非独占样本数百分比**|-   对于函数或模块，为此函数或模块的非独占样本数占分析运行期间所有样本数的百分比。<br />-   对于行或指令，为从中执行此行或指令的样本数占分析运行期间所有样本数的百分比。|  
|**独占样本数**|-   对于函数，为从中直接执行此函数的调用堆栈样本的数量；即此函数从中位于调用堆栈顶部的样本的数量。<br />-   对于模块，为模块中各个函数的独占样本数之和。<br />-   对于行或指令，为从中执行此行或指令的样本的数量。|  
|**独占样本数 %**|-   对于函数或模块，为此函数或模块的独占样本数占分析运行期间所有样本数的百分比。<br />-   对于行或指令，为从中执行此行或指令的样本数占分析运行期间所有样本数的百分比。|  
  
## 请参阅  
 [“模块”视图 \- 采样](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [“模块”视图 \- 检测](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [“模块”视图](../profiling/modules-view-instrumentation-data.md)