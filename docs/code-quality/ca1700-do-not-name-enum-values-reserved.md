---
title: "CA1700： 不要命名枚举值 &#39;保留 &#39; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2acfafaec213f619dbe8c3077ab5cc72bdfde88d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700： 不要命名枚举值 &#39;保留 &#39;
|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 枚举成员的名称包含单词"保留"。  
  
## <a name="rule-description"></a>规则说明  
 此规则假定当前不使用名称中包含“reserved”的枚举成员，而是将其作为一个占位符，以在将来的版本中重命名或移除它。 重命名或移除成员是一项重大更改。 不应指望用户只是因为其名称包含"保留"，也不能依赖用户读取或遵守的文档时，才会忽略该成员。 此外，由于保留的成员显示在对象浏览器和智能集成的开发环境中，它们可能会导致的混淆的成员实际上正在使用的相关。  
  
 而不是使用保留的成员，将添加到未来的版本中枚举的新成员。 在大多数情况下添加新成员不是一项重大更改，只要添加不会导致原始的成员，若要更改的值。  
  
 在有限数量的情况下添加成员是一项重大更改，即使原始成员保留其原始值。 主要原因是，新的成员无法返回从现有的代码路径而不会破坏使用的调用方`switch`(`Select`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 语句返回的值，级别包括整个成员列表中，并且，在引发的异常默认情况。 辅助问题是，客户端的代码可能不处理从反射的方法的行为更改如<xref:System.Enum.IsDefined%2A?displayProperty=fullName>。 相应地，如果要从现有方法中返回具有新的成员或由于较差的反射使用而发生的已知应用程序不兼容，唯一的不间断解决方案是：  
  
1.  添加新的枚举，其中包含原始列值和新成员。  
  
2.  将标记与在原始枚举<xref:System.ObsoleteAttribute?displayProperty=fullName>属性。  
  
 执行的任何外部可见的类型或公开原始枚举的成员相同的过程。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除或重命名的成员。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，为当前使用的成员或以前发布的库。  
  
## <a name="related-rules"></a>相关的规则  
 [CA2217：不要使用 FlagsAttribute 标记枚举](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712：不要将类型名用作枚举值的前缀](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028：枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008：枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027：用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md)