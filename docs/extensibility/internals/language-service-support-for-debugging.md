---
title: "语言服务支持以进行调试 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试器中，语言支持"
  - "调试支持的语言服务"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 语言服务支持以进行调试
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

语言服务可提供功能来支持通过调试器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> 接口。 这些功能包括验证断点并提供到表达式的列表 **自动** 窗口。  
  
 但是，您需要的表达式计算器，若要调试您的语言。 表达式计算器负责评估表达式，以在调试时生成的值。 有关实现 CLR 表达式计算器的信息，请参阅:  
  
-   [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [托管的表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## 编译器输出  
 编译器的类型确定您需要实现调试您的语言执行的操作。 如果您的编译器版本面向 Windows 操作系统，并编写一个.pdb 文件，您可以用本机代码调试引擎集成到 Visual Studio 调试程序。 如果您的编译器生成 Microsoft 中间语言 \(MSIL\)，您可以用托管代码调试引擎，还集成到 Visual Studio 调试程序。 如果您的编译器的目标系统的专有操作系统或不同的运行时环境，您需要编写您自己的调试引擎。  
  
 有关实现调试您的语言的详细信息，请参阅 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 在 Visual Studio Debugging SDK。