---
title: "“调用树”视图 - 探查器采样数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "采样分析方法, “调用关系树”视图"
  - "“调用关系树”视图"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# “调用树”视图 - 探查器采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“调用关系树”视图显示遍历所分析的应用程序的函数执行路径。  
  
> [!NOTE]
>  在 Windows 8 增强的安全功能和 Windows server 2012 要求已在 Visual Studio 探查器将收集有关这些平台的数据的方式的重大更改。  Windows 存储 app 还需要新的集合技术。  请参见 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 关系树的根是应用程序或组件的入口点。  每个函数节点都列出它调用的所有函数以及有关这些函数调用的性能数据。  
  
 “调用关系树”视图中的值对应于调用关系树中父函数所调用的函数实例。  百分比值是通过将函数实例值与分析运行期间的样本总数相比计算而得。  
  
## 突出显示执行热路径  
 “调用树”视图还可以展开和突出显示被采样频率最高的进程或函数的执行路径。  若要显示最活跃的路径，请右击进程或函数，然后单击**“展开热路径”**。  
  
## 设置调用关系树根节点  
 分析运行中的每个进程都显示为根节点。  若要设置“调用树”视图的开始节点，请右击要设置为开始节点的节点，然后选择**“设置根”**。  
  
 设置根节点后，将消除视图中除所选节点的子树之外的所有其他项。  若要将根节点重置为原始节点，请右击“调用树”视图窗口，然后选择**“重置根”**。  
  
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
|**级别**|此函数在调用树中的深度。  仅用于 [VSPerfReport](../profiling/vsperfreport.md) 命令行报告。|  
|**独占样本数**|调用树中的父函数调用此函数时此函数收集的样本数。  此数目不包括函数所调用的各个函数中收集的样本。|  
|**独占样本数 %**|调用树中父函数调用此函数时此函数的独占样本数占分析运行期间所有样本数的百分比。|  
|**非独占样本数**|调用树中的父函数调用此函数时此函数收集的样本数。  此数目包括函数所调用的各个函数中收集的样本。|  
|**非独占样本数百分比**|调用树中父函数调用此函数时此函数的非独占样本数占分析运行期间所有样本数的百分比。|  
  
## 请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [“调用关系树”视图 \- 采样](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [“调用关系树”视图 \- 检测](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [“调用关系树”视图](../profiling/call-tree-view-instrumentation-data.md)