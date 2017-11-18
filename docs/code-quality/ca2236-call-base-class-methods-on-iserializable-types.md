---
title: "CA2236： 对 ISerializable 类型的调用基类方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5379defde7ace66f43cad0983c9b14b554fb232
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236：对 ISerializable 类型调用基类方法
|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 某个类型派生于实现的类型<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口，并且以下条件之一为 true:  
  
-   该类型实现序列化构造函数中，即，构造函数与<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>，<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>参数签名，但不调用基类型的序列化构造函数。  
  
-   该类型实现<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法但不会调用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基类型的方法。  
  
## <a name="rule-description"></a>规则说明  
 在自定义序列化过程中，一个类型实现<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法以序列化其字段和序列化构造函数进行反序列化字段。 如果类型派生于实现的类型<xref:System.Runtime.Serialization.ISerializable>接口的基类型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化构造函数都应该调用到序列化/反序列化的基类型的字段。 否则为类型将不会序列化和反序列化正确。 请注意，是否派生的类型不添加任何新字段，类型不会不需要实现<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法，也不序列化构造函数或调用基类型等效的。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，调用基类型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>从相应的方法或序列化构造函数派生类型方法或构造函数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示满足该规则通过调用序列化构造函数的派生的类型和<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基本类的方法。  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2240：正确实现 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239：为可选字段提供反序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120：保护序列化构造函数](../code-quality/ca2120-secure-serialization-constructors.md)