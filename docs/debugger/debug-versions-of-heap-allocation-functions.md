---
title: "堆分配函数的调试版本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c05354363821d7da7c7ff38f1543900dcfa0c4e0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-versions-of-heap-allocation-functions"></a>堆分配函数的“Debug”版本
C 运行库包含堆分配函数的特殊“Debug”版本。 这些函数的名称与发行版本相同，只是追加了“_dbg”。 本主题用 `malloc` 和 `_malloc_dbg` 作为示例，描述 CRT 函数的发行版本和 _dbg 版本之间的差异。  
  
 当[_DEBUG](/cpp/c-runtime-library/debug)是定义，CRT 映射所有[malloc](/cpp/c-runtime-library/reference/malloc)调用[_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)。 因此，不需要用 `_malloc_dbg` 代替 `malloc` 来重写代码以获得调试时的好处。  
  
 但您可能希望显式调用 `_malloc_dbg`。 显式调用 `_malloc_dbg` 具有一些附加的好处：  
  
-   跟踪 `_CLIENT_BLOCK` 类型分配。  
  
-   存储分配请求所在的源文件和行号。  
  
 如果不希望将转换你`malloc`调用`_malloc_dbg`，你可以通过定义获取源文件信息[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)，这将导致预处理器到直接映射到的所有调用`malloc`到`_malloc_dbg`而不是依靠周围的包装器`malloc`。  
  
 若要跟踪客户端块中各种类型的分配，必须直接调用 `_malloc_dbg`，并将 `blockType` 参数设置为 `_CLIENT_BLOCK`。  
  
 如果未定义 _DEBUG，调用`malloc`不会受到干扰，则调用`_malloc_dbg`将解析为`malloc`的定义[_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)会忽略，并且源与相关的文件信息未提供分配请求。 因为 `malloc` 没有块类型参数，所以将对 `_CLIENT_BLOCK` 类型的请求作为标准分配处理。  
  
## <a name="see-also"></a>另请参阅  
 [CRT 调试方法](../debugger/crt-debugging-techniques.md)