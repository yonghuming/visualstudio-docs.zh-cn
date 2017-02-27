---
title: "调用方/被调用方视图 - 探查器采样数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "采样分析方法, “调用方/被调用方”视图"
  - "“调用方/被调用方”视图"
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 调用方/被调用方视图 - 探查器采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“调用方\/被调用方”视图显示有关所选函数及其父函数和子函数的分析信息。  “调用方\/被调用方”视图包含三个网格。  
  
 **“当前函数”**显示在中间网格内，用于显示有关所选函数的分析信息。  值包括对该函数采样的所有调用。  
  
 **“调用当前函数的函数”**显示在顶部网格内，用于显示各个调用方（父）函数对所选（当前）函数的值的作用。  
  
 **“由当前函数调用的函数”**显示在底部网格内，用于显示在当前函数调用被调用方（子）函数时，所选函数的子函数的相关分析信息。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
|列|描述|  
|-------|--------|  
|**进程 ID**|分析运行的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**模块名**|函数所在模块的名称。|  
|**模块路径**|函数所在模块的路径。|  
|**源文件**|包含函数定义的源文件。|  
|**函数名**|函数的完全限定名。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**函数地址**|函数的地址。|  
|**类型**|函数的上下文：<br /><br /> -   **0** \- 当前函数<br />-   **1** \- 调用当前函数的函数<br />-   **2** \- 当前函数调用的函数|  
|**根函数名**|当前函数的名称。|  
|**非独占样本数**|-   对于当前函数，为所收集（即使此函数或其某个子函数正在执行）的样本数。<br />-   对于调用方函数，为此函数调用当前函数时所收集的当前函数的非独占样本数。<br />-   对于被调用方函数，为当前函数调用此函数时收集的此函数的非独占样本数。|  
|**非独占样本数百分比**|此函数的非独占样本占分析运行期间所有样本的百分比。|  
|**独占样本数**|-   对于当前函数，为分析运行期间直接执行此函数时（即此函数位于调用堆栈顶部时）所收集的样本数。  独占计数内不计算此函数的子函数执行时所收集的样本。<br />-   对于调用方函数，为此函数调用当前函数时所收集的当前函数的独占样本数。<br />-   对于被调用方函数，为当前函数调用此函数时收集的此函数的独占样本数。|  
|**独占样本数 %**|此函数的独占样本占分析运行期间所有样本的百分比。|  
  
## 请参阅  
 [“调用方\/被调用方”视图 \- 采样](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [“调用方\/被调用方”视图 \- 检测](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [“调用方\/被调用方”视图](../profiling/caller-callee-view-instrumentation-data.md)