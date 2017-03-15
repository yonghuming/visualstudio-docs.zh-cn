---
title: "CA1032：实现标准异常构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1032：实现标准异常构造函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某类型扩展了 <xref:System.Exception?displayProperty=fullName>，但没有声明所有需要的构造函数。  
  
## 规则说明  
 异常类型必须实现下列构造函数：  
  
-   公共 NewException\(\)  
  
-   公共 NewException\(string\)  
  
-   公共 NewException\(string, Exception\)  
  
-   受保护或私有的 NewException\(SerializationInfo, StreamingContext\)  
  
 如果不能提供完整的构造函数集，要正确处理异常将变得比较困难。  例如，带有签名 `NewException(string, Exception)` 的构造函数用于创建由其他异常导致的异常。  如果没有此构造函数，则无法创建和引发包含内部（嵌套）异常的自定义异常的实例，而在此类情况下托管代码应执行此操作。  按照约定，前三个异常构造函数是公共的。  第四个构造函数在未密封类中是受保护的，而在密封类中是私有的。  有关更多信息，请参见[CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将缺少的构造函数添加到异常，并确保这些构造函数具有正确的可访问性。  
  
## 何时禁止显示警告  
 在冲突由使用公共构造函数的其他访问级别所导致时，可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例包含一个与该规则冲突的异常类型和一个正确实现的异常类型。  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]