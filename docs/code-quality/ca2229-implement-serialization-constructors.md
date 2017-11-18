---
title: "CA2229： 实现序列化构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d262718e6728a87cb955019fff0ce95db2b49d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229：实现序列化构造函数
|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 该类型实现<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口，不是委托或接口，并且以下条件之一为 true:  
  
-   类型不具有的构造函数的<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>对象和一个<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>对象 （序列化构造函数的签名）。  
  
-   类型是未密封，并且其序列化构造函数的访问修饰符不是受保护 （系列）。  
  
-   类型密封的其序列化构造函数的访问修饰符不是私有。  
  
## <a name="rule-description"></a>规则说明  
 此规则是适用于支持自定义序列化的类型。 如果它实现支持自定义序列化类型<xref:System.Runtime.Serialization.ISerializable>接口。 序列化构造函数需要反序列化，或重新创建已序列化使用的对象<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 要修复与该规则的冲突，请实现序列化构造函数。 对于密封类，请使构造函数成为私有；否则，请使构造函数成为受保护。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示与规则的冲突。 类型不会反序列化，并且在许多情况下不起作用。  
  
## <a name="example"></a>示例  
 下面的示例演示满足该规则的类型。  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>