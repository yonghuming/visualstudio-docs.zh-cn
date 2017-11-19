---
title: "示例实现局部变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c167c0a0f0a9dd0c14b92f27c0d9d862b5157072
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sample-implementation-of-locals"></a>局部变量的实现示例
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 下面是 Visual Studio 如何从表达式计算器 (EE) 获取的方法的局部变量的概述：  
  
1.  Visual Studio 会调用调试引擎 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)获取[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示的堆栈帧，包括局部变量的所有属性的对象。  
  
2.  `IDebugStackFrame2::GetDebugProperty`调用[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)以获取一个对象，描述在其中出现断点的方法。 DE 提供符号提供程序 ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md))，一个地址 ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md))，和联编程序 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md))。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`调用[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)与所提供`IDebugAddress`要获取对象[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)表示包含指定的地址的方法。  
  
4.  `IDebugContainerField`接口查询有关[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)接口。 它是此接口的访问的方法的局部变量。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`实例化类 (调用`CFieldProperty`示例中) 实现`IDebugProperty2`接口来表示该方法的局部变量。 `IDebugMethodField`对象放入此`CFieldProperty`对象连同`IDebugSymbolProvider`，`IDebugAddress`和`IDebugBinder`对象。  
  
6.  当`CFieldProperty`对象进行初始化， [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md)上调用`IDebugMethodField`对象以获取[FIELD_INFO](../../extensibility/debugger/reference/field-info.md)结构，其中包含有关方法本身的所有可显示信息.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`返回`CFieldProperty`对象作为`IDebugProperty2`对象。  
  
8.  Visual Studio 调用[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)对返回`IDebugProperty2`与筛选器的对象`guidFilterLocalsPlusArgs`。 这将返回[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)对象，其中包含该方法的局部变量。 此枚举通过调用填充[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)和[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)。  
  
9. Visual Studio 调用[下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)获取[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)对于每个本地的结构。 此结构包含的指针`IDebugProperty2`本地接口。  
  
10. Visual Studio 调用[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)对于每个本地获取局部变量的名称、 值和类型。 这是中显示的信息**局部变量**窗口。  
  
## <a name="in-this-section"></a>本节内容  
 [实现 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 描述的实现[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)。  
  
 [枚举局部](../../extensibility/debugger/enumerating-locals.md)  
 描述如何执行调用以枚举本地变量或自变量的调试引擎 (DE)。  
  
 [获取局部属性](../../extensibility/debugger/getting-local-properties.md)  
 描述如何执行调用以获取名称、 类型和值的一个或多个局部变量 DE。  
  
 [获取局部值](../../extensibility/debugger/getting-local-values.md)  
 讨论获取的值的局部变量需要评估上下文中的给定的联编程序对象的服务。  
  
 [计算局部](../../extensibility/debugger/evaluating-locals.md)  
 说明如何评估局部变量。  
  
## <a name="related-sections"></a>相关章节  
 [计算上下文](../../extensibility/debugger/evaluation-context.md)  
 提供当 DE 调用表达式计算器 (EE) 传递的参数。  
  
 [MyCEE 示例](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 演示一种用于创建 MyC 语言的表达式计算器的实现方式。  
  
## <a name="see-also"></a>另请参阅  
 [显示局部](../../extensibility/debugger/displaying-locals.md)