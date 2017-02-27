---
title: "IDebugExpressionEvaluator3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator3 接口"
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 增强的分析器目录树表示的表达式计算器 \(EE\)。  
  
## 语法  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## 调用方的说明  
 此版本的分析器传递符号提供程序和评估的帧的地址。  
  
## 方法  
 除了上方法 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) 接口，此接口实现了以下方法︰  
  
|方法|描述|  
|--------|--------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|将一个表达式字符串转换为分析的表达式给定符号提供程序和评估的帧的地址。|  
  
## 要求  
 标头︰ Ee.h  
  
 命名空间 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 程序集 ︰ Microsoft.VisualStudio.Debugger.Interop.dll