---
title: "Visual Studio 调试器可扩展性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [Visual Studio]，调试 SDK"
  - "调试 SDK"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Visual Studio 调试器可扩展性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 提供了完全交互式源代码调试器，提供一个功能强大且易于使用的工具，用于跟踪您的程序中的 bug。 调试器具有完整的支持 Visual Basic、 C\#、 C\/c \+ \+ 和 JavaScript。 但是，对于 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], ，即从可用 [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, 、 其他编程语言可以支持在调试器中的相同的丰富功能。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试器是常见的前端 （即，用户界面），接下来，特定于语言正在调试的调试组件。 对于新语言，所有所需的支持通过 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试器是创建必要的后端组件，如调试引擎 \(DE\)。 这正是 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 派上用场。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 包括所有的完整参考资料 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元素创建新 DE 所必需的。 另外，还包括一些示例和教程，可帮助您入门。  
  
 具有调试支持的语言项目系统的端到端示例，请参阅 [IronPython sample](http://msdn.microsoft.com/zh-cn/4c41695c-12c1-4670-b43b-d8d84c9e4089)。  
  
 下列各节描述如何通过使用扩展调试器 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
## 本节内容  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 描述什么 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试优惠以及如何安装 SDK。  
  
 [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 介绍从到分离 DE DE 准备您的程序的自定义的 DE 流程。  
  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 说明是否必须编写的表达式计算器。  
  
 [选择调试引擎实施策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 讨论如何实现您 DE。  
  
 [引用](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 文档 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 调试 API。  
  
 [示例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 包含公共语言运行时表达式计算器示例和调试引擎示例的链接。