---
title: "CA2208： 正确实例化自变量异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cb25017750ee95d55f1c776dea1f062f24ec22c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208：正确实例化自变量异常
|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 可能的原因包括以下情况下：  
  
-   异常类型，或派生自的默认 （无参数） 构造函数进行调用<xref:System.ArgumentException>。  
  
-   不正确的字符串自变量传递给参数化构造函数的异常类型，或派生自<xref:System.ArgumentException>。  
  
## <a name="rule-description"></a>规则说明  
 而不是调用默认构造函数，调用允许更有意义的异常消息，必须提供的构造函数重载之一。 异常消息应面向开发人员，并清楚地介绍错误条件以及如何更正或避免异常。  
  
 一个或两个字符串的构造函数的签名<xref:System.ArgumentException>和其派生的类型不一致相对于`message`和`paramName`参数。 请确保用正确的字符串自变量调用这些构造函数。 签名如下所示：  
  
 <xref:System.ArgumentException>(字符串`message`)  
  
 <xref:System.ArgumentException>(字符串`message`，字符串`paramName`)  
  
 <xref:System.ArgumentNullException>(字符串`paramName`)  
  
 <xref:System.ArgumentNullException>(字符串`paramName`，字符串`message`)  
  
 <xref:System.ArgumentOutOfRangeException>(字符串`paramName`)  
  
 <xref:System.ArgumentOutOfRangeException>(字符串`paramName`，字符串`message`)  
  
 <xref:System.DuplicateWaitObjectException>(字符串`parameterName`)  
  
 <xref:System.DuplicateWaitObjectException>(字符串`parameterName`，字符串`message`)  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用的构造函数的消息、 参数名称，或两者，并确保自变量类型的正确<xref:System.ArgumentException>调用。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，仅当参数化构造函数调用使用正确的字符串自变量。  
  
## <a name="example"></a>示例  
 下面的示例演示不正确实例化 ArgumentNullException 类型的实例的构造函数。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## <a name="example"></a>示例  
 下面的示例通过切换构造函数自变量中修复了上面的冲突。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]