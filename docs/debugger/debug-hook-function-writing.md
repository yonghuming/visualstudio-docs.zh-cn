---
title: "编写调试挂钩函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "调试挂钩函数"
  - "调试 [C++], CRT 调试支持"
  - "调试 [CRT], 调试挂钩函数"
  - "挂钩"
  - "挂钩, 调试"
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 编写调试挂钩函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本节描述了您可以编写的自定义调试挂钩函数，它允许您在调试器的正常处理中将代码插入某些预定义的点中。  
  
## 本节内容  
 [客户端块挂钩函数](../debugger/client-block-hook-functions.md)  
 提供有关编写某些函数的指导和原型，这些函数验证或报告正存储在 \_CLIENT\_BLOCK 块中的数据的内容。  
  
 [分配挂钩函数](../debugger/allocation-hook-functions.md)  
 定义分配挂钩函数，探讨它的不同用法，指出限制并提供原型。  
  
 [分配挂钩和 CRT 内存分配](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 描述分配挂钩函数在调用分配内部内存的 C 运行库函数时，在显式忽略 `_CRT_BLOCK` 块方面所受的限制。  本主题还用示例列出了分配挂钩不忽略 `_CRT_BLOCK` 块的后果，并描述如何更改默认分配挂钩函数 **CrtDefaultAllocHook**。  
  
 [报告挂钩函数](../debugger/report-hook-functions.md)  
 讨论 `_CrtSetReportHook`，可以使用它筛选报告以集中于特定的分配类型。  本主题还提供原型。  
  
## 相关章节  
 [CRT 调试技术](../debugger/crt-debugging-techniques.md)  
 链接到 C 运行库的调试技术，包括：使用 CRT 调试库、用于报告的宏、`malloc` 和 `_malloc_dbg` 之间的差异、编写调试挂钩函数以及 CRT 调试堆。