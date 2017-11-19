---
title: "实现表达式计算器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8cb80098edf4f05de550c8b8a22e0ed0649ca26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-an-expression-evaluator"></a>实现表达式计算器
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 计算表达式是相互作用的结果之间的调试引擎 (DE)、 符号提供程序 (SP)、 联编程序对象和表达式计算器 (EE) 本身。 四个组件由接口是一个组件实现的并且使用的另一个连接。  
  
 EE DE 中以字符串的形式从所需的表达式和分析类型或对其进行计算。 EE 实现以下接口，供 DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE 调用 DE，若要获取的符号和对象的值由提供的联编程序对象。 EE 使用以下接口，这些由 DE 实现接口：  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 EE 实现[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)。 `IDebugProperty2`提供用于描述表达式求值的结果，如本地变量、 一个基元或到 Visual Studio，然后显示中的相应信息的对象的机制**局部变量**， **监视**，或**即时**窗口。  
  
 SP 是提供给 EE DE 时系统会要求提供信息。 SP 可实现描述地址和域，如下面的接口和及其衍生产品的接口：  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE 使用所有这些接口。  
  
## <a name="in-this-section"></a>本节内容  
 [表达式计算器实施策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 定义了表达式计算器 (EE) 实现策略一个三步骤过程。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)