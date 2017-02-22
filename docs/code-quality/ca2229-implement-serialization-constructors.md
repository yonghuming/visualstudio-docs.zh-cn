---
title: "CA2229：实现序列化构造函数 | Microsoft Docs"
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
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229：实现序列化构造函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 该类型实现 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 接口，它不是委托或接口，并且满足下列条件之一：  
  
-   类型没有采用 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 对象和 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 对象（序列化构造函数的签名）的构造函数。  
  
-   类型未密封，其序列化构造函数的访问修饰符未受保护。  
  
-   类型是密封的，其序列化构造函数的访问修饰符不是私有的。  
  
## 规则说明  
 该规则与支持自定义序列化的类型相关。  如果一个类型实现 <xref:System.Runtime.Serialization.ISerializable> 接口，则该类型支持自定义序列化。  反序列化或重新创建已使用 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法序列化的对象时，需要序列化构造函数。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请实现序列化构造函数。  对于密封类，请使构造函数成为私有；否则，请使构造函数成为受保护。  
  
## 何时禁止显示警告  
 不要禁止显示与此规则的冲突。  类型是不能反序列化的，在许多情况下无法运行。  
  
## 示例  
 下面的示例演示一个满足该规则的类型。  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## 相关规则  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## 请参阅  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>