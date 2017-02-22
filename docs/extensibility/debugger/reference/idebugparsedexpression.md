---
title: "IDebugParsedExpression | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "IDebugParsedExpression 接口"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此接口表示准备要进行求值的已分析的表达式。  
  
## 语法  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## 实施者注意事项  
 表达式计算器实现此接口来表示分析的表达式，可供评估。  
  
## 调用方的说明  
 调用 [分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 返回此接口。  
  
## Vtable 顺序中的方法  
 下表显示的方法 `IDebugParsedExpression`。  
  
|方法|描述|  
|--------|--------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|分析的表达式的计算结果。|  
  
## 备注  
 当调用方就可以计算表达式时，它将调用 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 返回 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，其中包含的计算结果。 评估，分析，然后评估，使已分析的表达式可以进行多次评估，从而绕过耗时的过程分析该表达式的此两部分方法。  
  
## 要求  
 标头︰ ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [分析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)