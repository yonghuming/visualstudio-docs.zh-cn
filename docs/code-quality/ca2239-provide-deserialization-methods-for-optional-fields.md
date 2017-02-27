---
title: "CA2239：为可选字段提供反序列化方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2239：为可选字段提供反序列化方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 类型有一个使用 <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> 特性标记的字段，并且该类型没有提供反序列化事件处理方法。  
  
## 规则说明  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 特性对序列化没有影响；用该特性标记的字段已序列化。  但是，反序列化时该字段将被忽略，并保留与其类型关联的默认值。  应当声明反序列化事件处理程序，以便在反序列化过程中设置该字段。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请为该类型添加反序列化事件处理方法。  
  
## 何时禁止显示警告  
 如果应在反序列化过程中忽略该字段，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示带有可选字段和反序列化事件处理方法的类型。  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## 相关规则  
 [CA2236：对 ISerializable 类型调用基类方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：正确实现 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120：保护序列化构造函数](../Topic/CA2120:%20Secure%20serialization%20constructors.md)