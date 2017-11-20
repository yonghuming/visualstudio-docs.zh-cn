---
title: "使用代码分析工具来分析应用程序质量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 33ce03bb04df9dc3701f6d9acff5b73e9891334f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>使用代码分析工具分析应用程序质量
## <a name="in-this-section"></a>本节内容  
 [分析托管代码质量](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 针对托管代码的 Visual Studio 代码分析提供有关托管程序集的信息，例如 Microsoft .NET Framework 设计准则中规定的编程和设计规则的冲突。 警告消息标识任何相关的编程和设计问题，如有可能，还提供有关如何修复问题的信息。  
  
 [使用代码分析来分析 C/C++ 代码质量](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 C/C++ 代码分析工具为开发人员提供有关其 C/C++ 源代码中可能存在的缺陷的信息。 该工具报告的常见编码错误包括缓冲区溢出、内存未初始化、null 指针取消引用，以及内存和资源泄漏。  
  
 [使用规则集对代码分析规则进行分组](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 选择和创建*规则集*要应用于你的项目。  
  
 [代码分析应用程序错误](../code-quality/code-analysis-application-errors.md)  
 修复代码分析功能中的错误。  
  
 [利用团队项目签入策略提高代码质量](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 使用 Team Foundation 版本控制 (TFVC) 时，可以为团队项目创建签入策略，以强制执行会产生更有效的代码并实现更高效的团队开发的实践。 签入策略是在团队项目级别设置的，并在允许代码签入之前在开发人员计算机上强制实施的规则。  
  
### <a name="code-analysis-for-drivers"></a>驱动程序的代码分析  
 通过系统地分析驱动程序源代码，代码分析工具可以帮助提高驱动程序的稳定性和可靠性。  
  
 [使用代码分析工具来分析驱动程序质量](http://go.microsoft.com/fwlink/?LinkId=227618)  
 驱动程序代码分析是一个编译时静态验证工具，该工具可检测 C 和 C++ 程序中的基本编码错误，并且该工具包括一个专用模块，该模块设计用于检测（主要）内核模式驱动程序代码中的错误。 Static Driver Verifier (SDV) 是一个静态验证工具，可以系统分析 Windows 内核模式驱动程序的源代码。 SDV 确定驱动程序是否与 Windows 操作系统内核正确交互。  
  
 [驱动程序警告的代码分析](http://go.microsoft.com/fwlink/?LinkId=225920)  
 介绍驱动程序代码分析在驱动程序代码中检测到可能的错误时报告的警告。  
  
## <a name="related-tasks"></a>相关任务  
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 在此处插入说明。  
  
 [单元测试代码](../test/unit-test-your-code.md)  
 在此处插入说明。
