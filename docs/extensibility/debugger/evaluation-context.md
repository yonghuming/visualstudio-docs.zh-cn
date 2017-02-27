---
title: "评估上下文 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算、 上下文"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 评估上下文
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 当调试引擎 \(DE\) 调用表达式计算器 \(EE\) 时，三个参数传递给 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 确定用于查找和评估符号的上下文下, 表中所示。  
  
## 参数  
  
|参数|描述|  
|--------|--------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 接口，用于指定符号处理程序 \(SH\) 被用来标识该符号。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 接口，用于指定当前执行点。 这可以用于查找包含所执行的代码的方法。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 接口，可以用来查找的值和给定名称的符号的类型。|  
  
 `IDebugParsedExpression::EvaluateSync` 返回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 表示所得到的值和其类型的接口。  
  
## 请参阅  
 [键表达式计算器接口](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)