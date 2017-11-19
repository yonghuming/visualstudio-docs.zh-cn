---
title: "CA1032： 实现标准异常构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7300465ce9cef97cf322a7667e775852e22edb4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032：实现标准异常构造函数
|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 类型扩展<xref:System.Exception?displayProperty=fullName>和未声明所需的所有构造函数。  
  
## <a name="rule-description"></a>规则说明  
 异常类型必须实现以下构造函数：  
  
-   公共 NewException()  
  
-   公共 NewException(string)  
  
-   公共 NewException (string，异常)  
  
-   受保护或私有 NewException （SerializationInfo，StreamingContext）  
  
 如果不能提供完整的构造函数集，要正确处理异常将变得比较困难。 例如，具有签名的构造函数`NewException(string, Exception)`用于创建的其他异常导致的异常。 不能创建和引发自定义异常包含内部 （嵌套） 异常的实例此构造函数，这是托管的代码应在这种情况中执行操作。 前三个异常构造函数为公共的约定。 第四个构造函数是在未密封类中，受保护和在密封类中为私有。 有关详细信息，请参阅[CA2229： 实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将缺少的构造函数添加到异常，并确保它们具有正确的可访问性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果冲突引起的公共构造函数使用不同的访问级别。  
  
## <a name="example"></a>示例  
 下面的示例包含违反此规则的异常类型和正确实现异常类型。  
  
 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]