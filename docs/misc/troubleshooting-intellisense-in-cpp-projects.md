---
title: "C++ 项目 IntelliSense 疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ncb 文件"
  - "IntelliSense, C++ 项目中的失败疑难解答"
  - "ncb 文件"
  - "“IntelliSense”疑难解答"
  - "Visual C++ 疑难解答, IntelliSense"
ms.assetid: 72e4eb39-66d3-403d-8da7-00ed288a1899
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# C++ 项目 IntelliSense 疑难解答
在某些情况下，IntelliSense 会停止工作。  按照以下步骤来帮助确定 IntelliSense 不能在 C\+\+ 项目中正常工作的原因。  
  
### 调查 C\+\+ 项目中的 IntelliSense 失败  
  
1.  确保 Visual C\+\+ 项目不含任何编译错误。  
  
    1.  如果项目为生成文件项目，请参见[如何：对生成文件项目启用 IntelliSense](../Topic/How%20to:%20Enable%20IntelliSense%20for%20Makefile%20Projects.md)。  
  
2.  确保 stdafx.h 位于包含路径中。  有关 Visual C\+\+ 项目中的包含路径的更多信息，请参见 [\#include 指令](/visual-cpp/preprocessor/hash-include-directive-c-cpp) 和 [\/I（附加包含目录）](/visual-cpp/build/reference/i-additional-include-directories)。  
  
## IntelliSense 限制  
 在以下情况下，IntelliSense 不会在 C\+\+ 项目中工作：  
  
-   光标位于代码注释中。  
  
-   正在写字符串。  
  
-   在光标上方出现语法错误。  
  
-   该解决方案由托管 C\+\+ 语法或 C\+\+ 语法的早期托管扩展所组成。  
  
-   如果使用 `#include` 指令多次引用某个头文件，并且该头文件的含义因通过 `#define` 指令进行定义的各种宏状态而发生变化，则不完全支持 IntelliSense。  换言之，如果多次包括一个头文件，而该头文件的用法在不同宏状态下有所不同，则 IntelliSense 无法始终正常工作。  
  
## 请参阅  
 [Troubleshooting IntelliSense](http://msdn.microsoft.com/zh-cn/c1b3adb9-0d48-4770-a51e-392ed818c484)   
 [如何：组织生成的项目输出文件](../Topic/How%20to:%20Organize%20Project%20Output%20Files%20for%20Builds.md)