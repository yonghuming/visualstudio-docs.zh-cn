---
title: "CA2208：正确实例化参数异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208：正确实例化参数异常
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 可能的原因包括以下情况：  
  
-   调用了 [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True) 异常类型或其派生异常类型的默认（无参数）构造函数。  
  
-   将不正确的字符串参数传递给 [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True) 异常类型或其派生异常类型的参数化构造函数。  
  
## 规则说明  
 不调用默认构造函数，而是调用允许提供更有意义的异常消息的构造函数重载之一。  异常消息应面向开发人员，并明确说明错误情况以及如何更正或避免异常。  
  
 <xref:System.ArgumentException> 及其派生类型的一个和两个字符串构造函数的签名相对于 `message` 和 `paramName` 参数不一致。  确保使用正确的字符串参数调用这些构造函数。  签名如下：  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## 如何解决冲突  
 要修复与该规则的冲突，请调用采用消息、参数名称或二者的构造函数，并确保变量对于所调用的 <xref:System.ArgumentException> 的类型是正确的。  
  
## 何时禁止显示警告  
 如果使用正确字符串变量调用参数化构造函数，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例显示了一个构造函数，此构造函数错误地实例化 ArgumentNullException 类型的实例。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## 示例  
 下面的示例通过切换构造函数参数修复了上面的冲突。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]