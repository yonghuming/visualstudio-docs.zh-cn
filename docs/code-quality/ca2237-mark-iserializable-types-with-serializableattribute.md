---
title: "CA2237：以 SerializableAttribute 标记 ISerializable 类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237：以 SerializableAttribute 标记 ISerializable 类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 某外部可见的类型实现 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 接口，并且没有使用 <xref:System.SerializableAttribute?displayProperty=fullName> 特性标记该类型。  该规则忽略其基类型不可序列化的派生类型。  
  
## 规则说明  
 要被公共语言运行时识别为可序列化，必须使用 <xref:System.SerializableAttribute> 特性标记类型，即使该类型通过实现 <xref:System.Runtime.Serialization.ISerializable> 接口使用了自定义的序列化例程。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将 <xref:System.SerializableAttribute> 特性应用于该类型。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的异常类警告，因为这些异常类必须是可序列化的才能在应用程序域之间正常工作。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  取消对 <xref:System.SerializableAttribute> 特性行的注释可以满足该规则。  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## 相关规则  
 [CA2236：对 ISerializable 类型调用基类方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240：正确实现 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239：为可选字段提供反序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：保护序列化构造函数](../Topic/CA2120:%20Secure%20serialization%20constructors.md)