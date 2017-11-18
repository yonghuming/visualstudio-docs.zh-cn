---
title: "CA2105： 数组字段不应将只读 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfc20d1bb2ae34455c836219bb809221f2ca382e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105：数组字段不应为只读
|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 保存数组的公共或受保护字段被声明只读的。  
  
## <a name="rule-description"></a>规则说明  
 当你将`readonly`(`ReadOnly`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 修饰符添加到包含的数组，该字段的字段构造无法将更改为引用其他数组。 但是，可以更改在只读字段中存储的数组的元素。 做出决策或执行基于可以公开访问的只读数组的元素的操作的代码可能包含可利用的安全漏洞。  
  
 请注意，具有一个公共字段也违反了设计规则[CA1051： 不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要解决由该规则标识的安全漏洞，并依赖于可以公开访问的只读数组的内容。 强烈建议你使用以下过程之一：  
  
-   将替换不能更改的强类型集合的数组。 有关详细信息，请参阅<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>。  
  
-   将替换为返回专用数组的克隆的方法的公共字段。 你的代码不依赖于克隆，因为存在时不存在风险，如果进行了修改元素。  
  
 如果你选择第二种方法，它们不取代字段的属性为;属性返回数组产生负面影响性能。 有关详细信息，请参阅[CA1819： 属性不应返回数组](../code-quality/ca1819-properties-should-not-return-arrays.md)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 强烈建议不要使用此规则的警告排除。 几乎在任何情况下发生其中只读字段的内容并不重要。 如果这是你的方案这种情况，删除`readonly`而不是排除警告消息的修饰符。  
  
## <a name="example"></a>示例  
 此示例演示与该规则冲突的风险。 第一部分演示一个示例库，它有一个类型， `MyClassWithReadOnlyArrayField`，包含两个字段 (`grades`和`privateGrades`) 不安全。 字段`grades`是公共的而且因此容易受到任何调用方。 字段`privateGrades`是私有的但存在仍风险，因为它将返回到调用方通过`GetPrivateGrades`方法。 `securePrivateGrades`以通过安全方式公开字段`GetSecurePrivateGrades`方法。 它声明为私有，遵循良好的设计做法。 第二部分显示更改存储的值的代码`grades`和`privateGrades`成员。  
  
 示例类库显示在下面的示例。  
  
 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## <a name="example"></a>示例  
 下面的代码使用示例类库演示只读数组安全问题。  
  
 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 此示例中的输出为：  
  
 **之前篡改： 年级： 90，90，90 私有年级： 90，90，90 安全年级，90，90，90**  
**后篡改： 年级： 90、 555，90 私有年级： 90、 555，90 安全年级，90，90，90**   
## <a name="see-also"></a>另请参阅  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>