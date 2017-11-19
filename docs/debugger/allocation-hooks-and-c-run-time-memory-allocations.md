---
title: "分配挂钩和 C 运行时内存分配 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62a8be3b1a1c98a330efeb26d9a84e74f2334423
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>分配挂钩和 C 运行时内存分配
对分配挂钩函数的一个非常重要的限制是，当它们调用任何分配内部内存的 C 运行库函数时，必须显式忽略 `_CRT_BLOCK` 块（由 C 运行库函数内部进行的内存分配）。 可通过在分配挂钩函数起始包括如下代码来忽略 `_CRT_BLOCK` 块：  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果您的分配挂钩未忽略 `_CRT_BLOCK` 块，那么挂钩中调用的任何 C 运行库函数都会使程序陷入无穷循环。 例如，`printf` 执行内部分配。 如果挂钩代码调用`printf`，则产生的分配将导致挂钩同样，调用将调用**printf**再次，依此类推，直到堆栈溢出。 如果需要报告 `_CRT_BLOCK` 分配操作，回避该限制的一种方法是，使用 Windows API 函数而不是 C 运行时函数来进行格式化和输出。 因为 Windows API 不使用 C 运行库堆，所以它们不会使您的分配挂钩陷入无穷循环。  
  
 如果检查运行库源文件时，你将看到，默认分配挂钩函数， **CrtDefaultAllocHook** (只返回**TRUE**)，位于其自己的单独的文件DBGHOOK。C。 如果您希望您的分配挂钩，即使对于在你的应用程序之前执行的运行时启动代码的分配调用**主要**函数，您可以使用你自己的而不是替换此默认函数使用[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)。  
  
## <a name="see-also"></a>另请参阅  
 [编写调试挂钩函数](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 示例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)