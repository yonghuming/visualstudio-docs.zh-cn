---
title: "实现表达式计算器 | Microsoft Docs"
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
  - "表达式计算器"
  - "调试 [调试 SDK]，表达式计算器"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 实现表达式计算器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 计算的表达式是调试引擎 \(DE\)、 符号提供程序 \(SP\)、 联编程序对象和表达式计算器 \(EE\) 本身之间的复杂叠加而。 通过由一个组件实现并由另一个接口，四个组件进行连接。  
  
 EE 从 DE 中以字符串的形式获取一个表达式，表达式和解析或对其进行计算。 EE 实现由 DE 以下接口︰  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE 调用 DE，若要获取的符号和对象的值由提供的联编程序对象。 EE 使用由 DE 实现以下接口︰  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 EE 实现 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)。`IDebugProperty2` 提供用于描述表达式求值的结果，如本地变量、 基元或到 Visual Studio，然后显示中的相应信息的对象的机制 **局部变量**, ，**监视**, ，或 **即时** 窗口。  
  
 SP 是提供给 EE DE 当它要求的信息。 SP 实现接口，用于描述地址和域，如下面的接口和其派生类︰  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE 占用的所有这些接口。  
  
## 本节内容  
 [表达式计算器实施策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 定义了表达式计算器 \(EE\) 实施策略分为三步过程。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)