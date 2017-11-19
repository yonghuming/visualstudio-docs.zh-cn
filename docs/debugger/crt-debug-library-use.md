---
title: "CRT 调试库使用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2774eacfb0472145edb84d5c3becf77513ee986
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="crt-debug-library-use"></a>CRT 调试库使用
C 运行库提供广泛的调试支持。 若要使用 CRT 调试库之一，你必须与链接[/调试](/cpp/build/reference/debug-generate-debug-info)和使用进行编译**/MDd**， **/MTd**，或**/LDd**。  
  
## <a name="remarks"></a>备注  
 CRT 调试的主要定义和宏可在 CRTDBG.h 头文件中找到。  
  
 CRT 调试库中的函数在编译时带有调试信息 ([/Z7、 /Zd、 /Zi、 /ZI （调试信息格式）](/cpp/build/reference/z7-zi-zi-debug-information-format))，不进行优化。 某些函数包含断言以验证传递给它们的参数，并且提供源代码。 使用此类源代码，可以单步执行 CRT 函数，以确认这些函数按预期方式工作并检查错误的参数或内存状态。 （某些 CRT 技术是专有技术，不提供用于异常处理、浮点和少数其他例程的源代码。）  
  
 安装 Visual C++ 时，可以选择在硬盘上安装 C 运行库源代码。 如果不安装源代码，将需要 CD-ROM 才能单步执行 CRT 函数。  
  
 你可以使用的各种运行时库的详细信息，请参阅[C 运行时库](/cpp/c-runtime-library/crt-library-features)。  
  
## <a name="see-also"></a>另请参阅  
 [CRT 调试技术](../debugger/crt-debugging-techniques.md)   
 [/MD、 /MT、 /LD （使用运行时库）](/cpp/build/reference/md-mt-ld-use-run-time-library)