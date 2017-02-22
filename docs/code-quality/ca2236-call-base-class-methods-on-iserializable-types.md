---
title: "CA2236：对 ISerializable 类型调用基类方法 | Microsoft Docs"
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
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2236：对 ISerializable 类型调用基类方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 从另一个类型派生的类型实现 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 接口，并且满足下列条件之一：  
  
-   该类型实现序列化构造函数（即带 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>、<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 参数签名的构造函数），但是不调用基类型的序列化构造函数。  
  
-   该类型实现 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法，但是不调用基类型的 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法。  
  
## 规则说明  
 在自定义序列化过程中，某类型实现 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法以将其字段序列化，实现序列化构造函数以将字段反序列化。  如果该类型从实现 <xref:System.Runtime.Serialization.ISerializable> 接口的类型派生，则应当调用基类型 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法和序列化构造函数，以便对基类型的字段进行序列化和反序列化。  否则，该类型将不能正确地序列化和反序列化。  请注意，如果派生类型不添加任何新字段，则该类型不需要实现 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法或序列化构造函数，也不需要调用基类型等效项。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请从相应的派生类方法或构造函数调用基类型 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法或序列化构造函数。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示通过调用基类型的序列化构造函数和 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法来满足该规则的派生类型。  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## 相关规则  
 [CA2240：正确实现 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：为可选字段提供反序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：保护序列化构造函数](../Topic/CA2120:%20Secure%20serialization%20constructors.md)