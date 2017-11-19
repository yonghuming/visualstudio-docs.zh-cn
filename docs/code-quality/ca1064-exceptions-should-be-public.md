---
title: "CA1064： 异常应该是公共 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd39b4655f4a1bc98e408655e86fa1068820c9f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064：异常应该是公共的
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 非公共异常派生直接自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。  
  
## <a name="rule-description"></a>规则说明  
 内部异常仅在其自己的内部范围内可见。 当异常超出内部范围后，只能使用基异常来捕获该异常。 如果内部异常继承自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>，外部代码将没有足够的信息来了解如何处理异常。  
  
 但是，如果代码有更高版本用作基内部异常的公共异常，那么是合乎情理假定此代码进一步出将能够执行某些智能与使用基异常。 公共异常将包含与所提供的 T:System.Exception、 T:System.SystemException 或 T:System.ApplicationException 内容的详细信息。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 使该异常公共，或其派生从不是公共异常的内部异常<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果你确信在所有情况下，将在其自己的内部范围内捕获私有异常，禁止显示此规则的消息。  
  
## <a name="example"></a>示例  
 因为异常类直接从异常派生的并且是内部，则将引发此规则在第一个示例方法，FirstCustomException。 因为尽管直接从异常还派生类，类声明为公共规则不会触发 SecondCustomException 类上。 第三个类也不会触发该规则，因为它不是派生直接<xref:System.Exception?displayProperty=fullName>， <xref:System.SystemException?displayProperty=fullName>，或<xref:System.ApplicationException?displayProperty=fullName>。  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]