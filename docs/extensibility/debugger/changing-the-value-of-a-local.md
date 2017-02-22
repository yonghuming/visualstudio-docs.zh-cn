---
title: "更改本地值 | Microsoft Docs"
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
  - "调试 [调试 SDK]，表达式计算"
  - "表达式计算、 以编程方式更改值"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 更改本地值
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，这种实现表达式计算器不推荐使用。 有关实现 CLR 表达式计算器的信息，请参阅 [CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 当在的值字段中键入新值 **局部变量** 窗口中，调试程序包传递的字符串中，键入与表达式计算器 \(EE\)。 EE 计算此字符串中，它可以包含一个简单的值或表达式，并将所得到的值存储在关联的本地。  
  
 这是过程的本地的值更改的概述︰  
  
1.  用户输入新值之后，Visual Studio 会调用 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 上 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 与本地相关联的对象。  
  
2.  `IDebugProperty2::SetValueAsString` 执行下列任务︰  
  
    1.  计算要生成一个值的字符串。  
  
    2.  将绑定关联 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 对象来获取 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 对象。  
  
    3.  值转换为一系列字节。  
  
    4.  调用 [SetValue](../Topic/IDebugObject::SetValue.md) 值的字节数放入内存，因此正在调试的程序可以访问它们。  
  
3.  Visual Studio 刷新 **局部变量** 显示 \(请参阅 [显示局部变量](../../extensibility/debugger/displaying-locals.md) 有关的详细信息\)。  
  
 此过程还可用来更改中的变量的值 **监视** 窗口只不过它是 `IDebugProperty2` 对象而不是使用的本地值相关联 `IDebugProperty2` 与本地本身相关联的对象。  
  
## 本节内容  
 [更改值的实现示例](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 使用 MyCEE 示例逐步更改值的过程。  
  
## 请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [显示局部变量](../../extensibility/debugger/displaying-locals.md)