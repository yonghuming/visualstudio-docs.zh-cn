---
title: "CRT 调试库使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG 链接器选项 [C++]"
  - "/LDd 编译器函数 [C++]"
  - "/MDd 编译器选项 [C++]"
  - "/MTd 编译器选项 [C++]"
  - "crtdbg.h 文件"
  - "调试库"
  - "DEBUG 链接器选项 [C++]"
  - "调试 [CRT], CRT 调试库"
  - "LDd 编译器函数 [C++]"
  - "库, CRT 调试库"
  - "MDd 编译器选项 [C++]"
  - "MTd 编译器选项 [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# CRT 调试库使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C 运行库提供广泛的调试支持。  若要使用 CRT 调试库之一，必须链接 [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)，并用 **\/MDd**、**\/MTd** 或 **\/LDd** 编译。  
  
## 备注  
 CRT 调试的主要定义和宏可在 CRTDBG.h 头文件中找到。  
  
 CRT 调试库中的函数编译时带有调试信息（[\/Z7、\/Zd、\/Zi、\/ZI（调试信息格式）](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)），不进行优化。  某些函数包含断言以验证传递给它们的参数，并且提供源代码。  使用此类源代码，可以单步执行 CRT 函数，以确认这些函数按预期方式工作并检查错误的参数或内存状态。（某些 CRT 技术是专有技术，不提供用于异常处理、浮点和少数其他例程的源代码。）  
  
 安装 Visual C\+\+ 时，可以选择在硬盘上安装 C 运行库源代码。  如果不安装源代码，将需要 CD\-ROM 才能单步执行 CRT 函数。  
  
 有关可以使用的各种运行库的更多信息，请参见 [C 运行库](/visual-cpp/c-runtime-library/crt-library-features)。  
  
## 请参阅  
 [CRT 调试方法](../debugger/crt-debugging-techniques.md)   
 [\/MD、\/MT、\/LD（使用运行库）](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)