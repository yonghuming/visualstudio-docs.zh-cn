---
title: "“行”视图 - 探查器采样数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“行”视图"
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# “行”视图 - 探查器采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

采样数据的“行”视图列出分析运行期间收集样本时所执行语句的性能数据。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
 在源文件中，一个语句可以跨多个行，并且一行可以包括多个语句。  语句由以下数据标识：  
  
-   包含函数语句的源文件。  
  
-   包含该语句的函数。  
  
-   该语句的起始源代码行。  
  
-   该语句的起始源代码行中的字符。  
  
-   该语句的结束源代码行。  
  
-   该语句的结束源代码行中的字符。  
  
 “行名”列提供一串可排序的标识符数据。  
  
 根据定义，语句不调用其他函数。  因此，仅列出独占值。  
  
|列|说明|  
|-------|--------|  
|**进程 ID**|分析运行的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**模块名**|函数行所在模块的名称。|  
|**模块路径**|函数行所在模块的路径。|  
|**源文件**|函数行所在的源文件。|  
|**函数名**|函数名。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**函数地址**|函数的起始地址。|  
|**源行的开始位置**|源文件中开始收集此样本的行号。|  
|**源行的结束位置**|源文件中结束收集此样本的行号。|  
|**源字符的开始位置**|源文件行中开始收集此样本的字符的偏移量。|  
|**源字符的结束位置**|源文件行中结束收集此样本的字符的偏移量。|  
|**行名**|由探查器生成的行标识符，具有以下语法：`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number End`,`Character End`\]**\]**|  
|**独占样本数**|执行此函数行时收集的样本总数。|  
|**独占样本数 %**|执行函数行期间收集的样本数占分析运行期间所有样本数的百分比。|  
  
## 请参阅  
 [“行”视图 \- 采样](../profiling/lines-view-dotnet-memory-sampling-data.md)