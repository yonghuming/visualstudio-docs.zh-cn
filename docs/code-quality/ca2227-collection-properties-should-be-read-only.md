---
title: "CA2227：集合属性应为只读 | Microsoft Docs"
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
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2227：集合属性应为只读
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|类别|Microsoft.Usage|  
|是否重大更改|是|  
  
## 原因  
 在外部可见的可写属性是实现 <xref:System.Collections.ICollection?displayProperty=fullName> 的类型。  数组、索引器（名为“Item”的属性）和权限集都将被该规则忽略。  
  
## 规则说明  
 使用可写的集合属性，用户可以将该集合替换为完全不同的集合。  只读属性禁止替换该集合，但仍允许设置单个成员。  如果将替换该集合作为一个目标，则首选的设计模式是包括两个方法，一个用来移除该集合中的所有元素，另一个用来重新填充该集合。  有关此模式的示例，请参见 <xref:System.Collections.ArrayList?displayProperty=fullName> 类的 <xref:System.Collections.ArrayList.Clear%2A> 和 <xref:System.Collections.ArrayList.AddRange%2A> 方法。  
  
 二进制序列化和 XML 序列化均支持作为集合的只读属性。  对于实现 <xref:System.Collections.ICollection> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName>，以便可序列化的类型，<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 类有特定要求。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将该属性设置为只读，如果设计需要的话，还添加一些用来清除和重新填充该集合的方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个具有可写集合属性的类型并演示如何直接替换该集合。  另外，还演示了使用 `Clear` 和 `AddRange` 方法替换只读集合属性的首选方式。  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## 相关规则  
 [CA1819：属性不应返回数组](../code-quality/ca1819-properties-should-not-return-arrays.md)