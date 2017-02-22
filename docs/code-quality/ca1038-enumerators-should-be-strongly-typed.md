---
title: "CA1038：枚举数应强类型化 | Microsoft Docs"
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
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038：枚举数应强类型化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某公共类型或受保护类型实现 <xref:System.Collections.IEnumerator?displayProperty=fullName>，但未提供 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 属性的强类型版本。  该规则中免除了从以下类型派生的类型：  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## 规则说明  
 此规则要求 <xref:System.Collections.IEnumerator> 实现还提供 <xref:System.Collections.IEnumerator.Current%2A> 属性的强类型版本，以使用户在使用该接口提供的功能时不必将返回值强制转换为强类型。  该规则假定实现 <xref:System.Collections.IEnumerator> 的类型包含强于 <xref:System.Object> 的类型的实例集合。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请显式实现接口属性（将其声明为 `IEnumerator.Current`）。  添加被声明为 `Current` 的公共强类型版本的属性，使其返回强类型对象。  
  
## 何时禁止显示警告  
 在实现基于对象的枚举数以与基于对象的集合（如二叉树）一起使用时，可以禁止显示此规则发出的警告。  扩展新集合的类型将定义强类型枚举数并公开强类型属性。  
  
## 示例  
 下面的示例演示实现强类型 <xref:System.Collections.IEnumerator> 类型的正确方法。  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## 相关规则  
 [CA1035：ICollection 实现含有强类型成员](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039：列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## 请参阅  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>