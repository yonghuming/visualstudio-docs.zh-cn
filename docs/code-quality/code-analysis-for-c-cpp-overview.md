---
title: "C/C++ 代码分析概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "#pragma 指令, 代码分析"
  - "批注, 代码分析"
  - "生成集成, 代码分析"
  - "C, 代码分析"
  - "C/C++ 代码分析"
  - "C++, 代码分析"
  - "签入策略, 代码分析"
  - "代码分析工具"
  - "代码分析, C/C++"
  - "命令行, 代码分析"
  - "IDE, 代码分析"
  - "pragma 指令, 代码分析"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ 代码分析概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C\/C\+\+ 代码分析工具为开发人员提供了有关他们的 C\/C\+\+ 源代码中可能存在的缺陷的信息。  工具报告的常见编码错误包括缓冲区溢出、内存未初始化、null 指针取消引用以及内存和资源泄漏。  
  
## IDE（集成开发环境）集成  
 分析工具与 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 完全集成，以方便开发人员使用。  在生成过程中，针对源代码生成的任何警告都显示在“错误列表”中。  您可以导航到导致警告的源代码，还可以查看其他信息，如问题的原因和可能的解决方法。  
  
## \#pragma 支持  
 开发人员可以使用 `#pragma` 指令将警告作为错误处理；还可以启用或禁用警告，以及禁止显示单个代码行的警告。  有关更多信息，请参见[How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/zh-cn/910b8518-71f1-4b2e-b012-70647795642a)。  
  
## 批注支持  
 批注可以提高代码分析的准确性。  批注可提供有关函数参数及返回类型的 pre（前置）条件和 post（后置）条件的其他信息。  有关更多信息，请参见[如何：使用 \_\_analysis\_assume 指定其他代码信息](../Topic/How%20to:%20Specify%20Additional%20Code%20Information%20by%20Using%20__analysis_assume.md)。  
  
## 作为签入策略的一部分运行分析工具  
 您可能要求源代码所有签入行为满足特定的策略。  尤其是，您需要确保分析作为最近本地生成的一个步骤来运行。  有关启用代码分析签入策略的更多信息，请参见[创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)。  
  
## Team Build 集成  
 您可以使用生成系统的集成功能在 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 生成过程中运行代码分析工具。  有关更多信息，请参见[生成应用程序](../Topic/Build%20the%20application.md)。  
  
## 命令行支持  
 分析工具是与开发环境完全集成的，此外，开发人员还可以从命令行使用分析工具，如下面的示例所示：  
  
 `C:\>cl /analyze Sample.cpp`