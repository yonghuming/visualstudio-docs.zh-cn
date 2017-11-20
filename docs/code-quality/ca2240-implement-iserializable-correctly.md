---
title: "CA2240： 实现 ISerializable 正确 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e3f9ba0e3cb182ec08dd802dc87728a0fb9dc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240：正确实现 ISerializable
|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 外部可见的类型是可分配给<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口以及以下条件之一为 true:  
  
-   类型继承，但不重写<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法和类型声明的实例字段不会将其标记为<xref:System.NonSerializedAttribute?displayProperty=fullName>属性。  
  
-   未密封的类型和该类型实现<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>不是外部可见的且可重写的方法。  
  
## <a name="rule-description"></a>规则说明  
 实例中继承的类型声明的字段<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>接口未自动包含在序列化过程。 若要包括的字段，类型必须实现<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化构造函数。 如果字段不应序列化，应用<xref:System.NonSerializedAttribute>属性要显式指示这一决定的字段。  
  
 未密封的实现的类型中<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>应是外部可见的方法。 因此，该方法可以由派生类型，调用，并且是可重写。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法可见且可以重写，并确保所有实例字段都包含在序列化过程中或者使用显式标记<xref:System.NonSerializedAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示两种可序列化的类型与该规则冲突。  
  
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## <a name="example"></a>示例  
 下面的示例通过提供可替代的实现修复前面两个冲突<xref:System.Runtime.Serialization.ISerializable.GetObjectData>Book 类和提供的实现中的`GetObjectData`库类。  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA2236：对 ISerializable 类型调用基类方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238：正确实现序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235：标记所有不可序列化的字段](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237：以 SerializableAttribute 标记 ISerializable 类型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239：为可选字段提供反序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120：保护序列化构造函数](../code-quality/ca2120-secure-serialization-constructors.md)  
