---
title: "CA2235：标记所有不可序列化的字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2235：标记所有不可序列化的字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 在可以序列化的类型中声明了类型不可序列化的实例字段。  
  
## 规则说明  
 可序列化类型是使用 <xref:System.SerializableAttribute?displayProperty=fullName> 特性标记的类型。  当类型被序列化时，如果类型包含一个类型不可序列化的实例字段，则会引发 <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 异常。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将 <xref:System.NonSerializedAttribute?displayProperty=fullName> 特性应用于不可序列化的字段。  
  
## 何时禁止显示警告  
 只有当声明了允许序列化和反序列化字段实例的 <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 类型时，才能禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型和一个满足该规则的类型。  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## 相关规则  
 [CA2236：对 ISerializable 类型调用基类方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：正确实现 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：为可选字段提供反序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：保护序列化构造函数](../Topic/CA2120:%20Secure%20serialization%20constructors.md)