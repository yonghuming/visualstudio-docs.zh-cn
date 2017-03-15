---
title: "堆分配函数的“Debug”版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC 宏"
  - "_malloc_dbg 函数"
  - "调试 [CRT], 堆分配函数"
  - "调试内存泄漏, CRT 调试库功能"
  - "堆分配, 调试"
  - "malloc 函数"
  - "内存泄漏, CRT 调试库功能"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# 堆分配函数的“Debug”版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C 运行库包含堆分配函数的特殊“Debug”版本。  这些函数的名称与发行版本相同，只是追加了“\_dbg”。  本主题用 `malloc` 和 `_malloc_dbg` 作为示例，描述 CRT 函数的发行版本和 \_dbg 版本之间的差异。  
  
 定义 [\_DEBUG](/visual-cpp/c-runtime-library/debug) 后，CRT 会将所有 [malloc](/visual-cpp/c-runtime-library/reference/malloc) 调用映射到 [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg)。  因此，不需要用 `_malloc_dbg` 代替 `malloc` 来重写代码以获得调试时的好处。  
  
 但您可能希望显式调用 `_malloc_dbg`。  显式调用 `_malloc_dbg` 具有一些附加的好处：  
  
-   跟踪 `_CLIENT_BLOCK` 类型分配。  
  
-   存储分配请求所在的源文件和行号。  
  
 如果不希望将 `malloc` 调用转换为 `_malloc_dbg`，可以通过定义 [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) 来获取源文件信息，而这导致预处理器将对 `malloc` 的所有调用直接映射到 `_malloc_dbg`，而不是依赖 `malloc` 周围的包装器。  
  
 若要跟踪客户端块中各种类型的分配，必须直接调用 `_malloc_dbg`，并将 `blockType` 参数设置为 `_CLIENT_BLOCK`。  
  
 未定义 \_DEBUG 时，对 `malloc` 的调用将不受妨碍，并且对 `_malloc_dbg` 的调用将被解析为 `malloc`，忽略 [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) 的定义，并且不提供与分配请求有关的源文件信息。  因为 `malloc` 没有块类型参数，所以将对 `_CLIENT_BLOCK` 类型的请求作为标准分配处理。  
  
## 请参阅  
 [CRT 调试方法](../debugger/crt-debugging-techniques.md)