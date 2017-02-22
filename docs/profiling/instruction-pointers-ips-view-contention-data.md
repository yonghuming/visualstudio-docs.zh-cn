---
title: "指令指针 (IP) 视图 - 探查器争用数据 | Microsoft Docs"
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
  - "“指令指针”视图"
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 指令指针 (IP) 视图 - 探查器争用数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

争用数据的 IP 视图列出了在分析运行中被阻止执行的程序集指令的数据。  
  
 下表说明“指令指针”视图中的列的值。  
  
|列|说明|  
|-------|--------|  
|**独占阻塞的时间**|函数中阻塞的时间。|  
|**独占阻塞的时间百分比**|执行指令时的阻塞时间所占的百分比。|  
|**独占争用**|执行指令时发生的争用数。|  
|**独占争用数百分比**|执行指令时发生的争用占分析运行中所有争用的百分比。|  
|**函数地址**|函数在加载的二进制文件中的起始内存地址。|  
|**函数名**|指令所在函数的名称。|  
|**指令地址**|指令在加载的二进制文件中的内存地址。|  
|**函数行号**|函数在源文件中的起始行号。|  
|**模块名**|指令所在模块的名称。|  
|**模块路径**|指令所在模块的路径。|  
|**进程 ID**|所分析进程的进程 ID \(PID\)。|  
|**进程名**|进程的名称。|  
|**源字符的开始位置**|指令的起始源文件行的字符偏移量。|  
|**源字符的结束位置**|指令的结束源文件行的字符偏移量。|  
|**源文件**|指令所在的源文件。|  
|**源行的开始位置**|此指令在源文件中的起始行号。|  
|**源行的结束位置**|此指令在源文件中的结束行号。|  
  
## 请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [“指令指针”\(IP\) 视图](../profiling/instruction-pointers-ips-view.md)   
 [“指令指针”\(IP\) 视图 \- 采样](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [“指令指针”\(IP\) 视图](../profiling/instruction-pointers-ips-view-sampling-data.md)