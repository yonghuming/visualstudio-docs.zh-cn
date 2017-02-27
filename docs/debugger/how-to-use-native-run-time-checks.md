---
title: "如何：使用本机运行时检查 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/O 编译器选项, /RTC 选项"
  - "/RTC 编译器选项 [C++], /O 编译器选项"
  - "数组 [Visual Studio], 调试"
  - "调试器, 本机运行时检查"
  - "调试器, 运行时错误"
  - "调试数组"
  - "本机运行时检查"
  - "O 编译器选项, /RTC 选项"
  - "优化生成选项"
  - "RTC 编译器选项, /O 编译器选项"
  - "运行时检查"
  - "运行时检查, 本机"
  - "运行时错误, 调试"
  - "运行时错误, 错误检查"
  - "runtime_checks 杂注"
  - "堆栈指针"
  - "堆栈指针, 损坏"
  - "堆栈, 指针损坏"
  - "变量 [调试器], 捕捉未初始化局部变量上的依赖项"
  - "变量 [调试器], 丢失数据"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：使用本机运行时检查
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual C\+\+ 中，可以使用本机 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) 捕获常见的运行时错误，例如：  
  
-   堆栈指针损坏。  
  
-   本地数组溢出。  
  
-   堆栈损坏。  
  
-   未初始化的局部变量上的依赖项。  
  
-   较短变量赋值的数据丢失。  
  
 如果使用带有优化 \(**\/RTC**\) 版本的 **\/O**，将导致编译器错误。 如果在优化版本中使用 `runtime_checks` 杂注，则该杂注无效。  
  
 调试启用了运行时检查的程序时，如果出现运行时错误，该程序的默认操作是停止并切换到调试器。 可以更改任何运行时检查的此默认行为。 有关详细信息，请参阅 [管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 下面的过程介绍了如何在调试版本中启用本机运行时检查，以及如何修改本机运行时检查的行为。  
  
 本节的其他主题提供了有关以下方面的信息：  
  
-   [用 C 运行库自定义运行时检查](../debugger/native-run-time-checks-customization.md)  
  
-   [使用无 C 运行库的运行时检查](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### 在调试版本中启用本机运行时检查  
  
-   使用 **\/RTC** 选项，并与 C 运行库（如 \/MDd）调试版链接。  
  
### 更改本机运行时检查操作  
  
-   使用 `runtime_checks` 杂注。  
  
## 请参阅  
 [使用 Visual Studio 进行调试](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [运行时错误检查](/visual-cpp/c-runtime-library/run-time-error-checking)