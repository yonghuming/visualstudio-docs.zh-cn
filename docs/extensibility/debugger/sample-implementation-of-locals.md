---
title: "局部变量的实现示例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "调试 [调试 SDK]，本地变量"
  - "表达式计算、 本地变量"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 局部变量的实现示例
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 下面是 Visual Studio 如何将从表达式计算器 \(EE\) 获取一种方法的局部变量的概述:  
  
1.  Visual Studio 会调用调试引擎 \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 获取 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 表示包括局部变量的堆栈帧的所有属性的对象。  
  
2.  `IDebugStackFrame2::GetDebugProperty` 调用 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 来获取一个对象，描述在其中出现断点的方法。 DE 提供符号提供程序 \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\)，一个地址 \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\)，和联编程序 \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\)。  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` 调用 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 与所提供 `IDebugAddress` 对象以获取 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 表示包含指定的地址的方法。  
  
4.  `IDebugContainerField` 接口查询有关 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 接口。 它是使该方法的局部变量可以访问此界面。  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` 实例化一个类 \(称为 `CFieldProperty` 示例中\)，用于实现 `IDebugProperty2` 接口来表示该方法的局部变量。`IDebugMethodField` 对象放在此 `CFieldProperty` 对象连同 `IDebugSymbolProvider`, ，`IDebugAddress` 和 `IDebugBinder` 对象。  
  
6.  当 `CFieldProperty` 初始化对象时， [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) 上调用 `IDebugMethodField` 对象来获取 [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) 结构，其中包含有关该方法本身的所有可显示信息。  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` 返回 `CFieldProperty` 对象作为 `IDebugProperty2` 对象。  
  
8.  Visual Studio 调用 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 对返回 `IDebugProperty2` 与筛选器的对象 `guidFilterLocalsPlusArgs`。 这将返回 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 对象，其中包含该方法的局部变量。 此枚举由调用填充 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 和 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)。  
  
9. Visual Studio 调用 [下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 获取 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 每个本地的结构。 此结构包含一个指向 `IDebugProperty2` 本地接口。  
  
10. Visual Studio 调用 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 对于每个本地若要获取的本地名称、 值和类型。 这是中显示的信息 **局部变量** 窗口。  
  
## 本节内容  
 [实现 GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 介绍的实现 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)。  
  
 [枚举局部变量](../../extensibility/debugger/enumerating-locals.md)  
 描述如何调试引擎 \(DE\) 调用一次枚举本地变量或参数。  
  
 [获取本地属性](../../extensibility/debugger/getting-local-properties.md)  
 描述如何执行调用以获取名称、 类型和值的一个或多个局部变量 DE。  
  
 [获取本地值](../../extensibility/debugger/getting-local-values.md)  
 讨论获取的值的局部变量需要的评估上下文由给定的联编程序对象提供服务。  
  
 [评估局部变量](../../extensibility/debugger/evaluating-locals.md)  
 说明如何评估局部变量。  
  
## 相关章节  
 [评估上下文](../../extensibility/debugger/evaluation-context.md)  
 提供当 DE 调用表达式计算器 \(EE\) 传递的参数。  
  
 [MyCEE Sample](http://msdn.microsoft.com/zh-cn/624a018b-9179-402f-9d48-3aec87b48f4f)  
 演示一个实现方法创建 MyC 语言的表达式计算器。  
  
## 请参阅  
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)