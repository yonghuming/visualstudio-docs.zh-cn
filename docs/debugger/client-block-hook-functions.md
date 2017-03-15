---
title: "客户端块挂钩函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetDumpClient 函数"
  - "客户端块, 挂钩函数"
  - "客户端块, 验证和报告数据"
  - "调试 [C++], 挂钩函数"
  - "挂钩, 客户端块"
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 客户端块挂钩函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果想要验证或报告存储在 `_CLIENT_BLOCK` 块中的数据的内容，可以专为此目的编写函数。  如同 CRTDBG.H 中所定义的，所编写的函数必须有与下面类似的原型：  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 换句话说，您的挂钩函数应接受一个 **void** 指针（指向分配块的起始），以及一个 **size\_t** 类型值（指示分配大小），并返回 `void`。  除此之外，其内容由您决定。  
  
 使用 [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) 安装了挂钩函数后，每次转储 `_CLIENT_BLOCK` 块时都将调用该挂钩函数。  然后，可以使用 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) 获取有关转储块的类型或子类型的信息。  
  
 您传递给 `_CrtSetDumpClient` 的指向函数的指针是 **\_CRT\_DUMP\_CLIENT** 类型，如 CRTDBG.H 中所定义：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## 请参阅  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/zh-cn/21e1346a-6a17-4f57-b275-c76813089167)   
 [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)