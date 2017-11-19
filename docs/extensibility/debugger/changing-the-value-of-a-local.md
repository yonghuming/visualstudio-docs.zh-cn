---
title: "更改的本地值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78affeb358200599d925b9b70df3ae945759054c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-value-of-a-local"></a>更改本地的值
> [!IMPORTANT]
>  在 Visual Studio 2015 中，已弃用这种方式实施表达式计算器。 有关实现 CLR 表达式计算器的信息，请参阅[CLR 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 新值的值字段中的类型时**局部变量**窗口中，调试包传递字符串，字符串类型，向表达式计算器 (EE)。 EE 计算此字符串，其中可以包含一个简单的值或表达式，并将生成的值存储在关联的本地。  
  
 这是过程的本地的值更改的概述：  
  
1.  用户输入新值后，Visual Studio 会调用[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)上[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)本地与关联的对象。  
  
2.  `IDebugProperty2::SetValueAsString`执行以下任务：  
  
    1.  要生成的值的字符串的计算结果。  
  
    2.  将绑定关联[IDebugField](../../extensibility/debugger/reference/idebugfield.md)对象以获取[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)对象。  
  
    3.  将值转换为一系列字节。  
  
    4.  调用[SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md)放入内存的值的字节，因此被调试的程序可以访问它们。  
  
3.  Visual Studio 刷新**局部变量**显示 (请参阅[显示局部变量](../../extensibility/debugger/displaying-locals.md)有关详细信息)。  
  
 此过程还可用来更改中的变量的值**监视**窗口，只不过它是`IDebugProperty2`对象而不是本地的值相关联`IDebugProperty2`本地与关联的对象本身。  
  
## <a name="in-this-section"></a>本节内容  
 [更改值的实现示例](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 使用 MyCEE 示例来单步执行更改值的过程。  
  
## <a name="see-also"></a>另请参阅  
 [编写 CLR 表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [显示局部](../../extensibility/debugger/displaying-locals.md)