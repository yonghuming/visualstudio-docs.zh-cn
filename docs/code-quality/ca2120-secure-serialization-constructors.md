---
title: "CA2120： 保护序列化构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e1896bc8f2c9c15c4aa7b9c7ec323412d494db0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120：保护序列化构造函数
|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 该类型实现<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口不是委托或接口，并声明的程序集中的允许部分受信任的调用方。 该类型具有的构造函数的<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>对象和一个<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>对象 （序列化构造函数的签名）。 此构造函数不受安全检查，但保护一个或多个类型中的正则构造函数。  
  
## <a name="rule-description"></a>规则说明  
 此规则是适用于支持自定义序列化的类型。 如果它实现支持自定义序列化类型<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口。 序列化构造函数是必需的并用于反序列化，或重新创建已序列化使用的对象<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法。 序列化构造函数分配和初始化对象，因为正则构造函数中存在的安全检查也必须存在上序列化构造函数。 如果违反了此规则，否则无法创建实例的调用方可以使用序列化构造函数来执行此操作。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，保护具有相同保护其他构造函数的安全需求的序列化构造函数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示与规则的冲突。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类型。  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>