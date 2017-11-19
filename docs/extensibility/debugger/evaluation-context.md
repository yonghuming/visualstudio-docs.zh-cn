---
title: "评估上下文 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a44d7ce7cffa2afc40971b0ea6f88a6f62617f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="evaluation-context"></a>评估上下文
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 当调试引擎 (DE) 调用表达式计算器 (EE) 时，三个自变量传递给[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)确定用于查找和评估符号，上下文下, 表中所示。  
  
## <a name="arguments"></a>参数  
  
|参数|描述|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)接口，用于指定符号处理程序 (SH) 要用于标识符号。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)接口，用于指定执行的当前点。 这可以用于查找包含所执行的代码的方法。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)可用于查找的值和在给定其名称的符号的类型的接口。|  
  
 `IDebugParsedExpression::EvaluateSync`返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示生成的值和其类型的接口。  
  
## <a name="see-also"></a>另请参阅  
 [键表达式计算器接口](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)