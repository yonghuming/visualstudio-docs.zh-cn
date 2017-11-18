---
title: "CA1023： 索引器不应是多维 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3b677f4cde4a38b2e682e36090e7a86f68e4fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023：索引器不应是多维的
|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护类型包含公共或受保护的索引器使用多个索引。  
  
## <a name="rule-description"></a>规则说明  
 索引器，即索引属性，应使用一个索引。 多维索引器会大大降低库的可用性。 如果在设计上要求多个索引，请重新考虑是否类型表示的逻辑数据存储区。 如果没有，请使用一种方法。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改设计，以使用长整型或字符串索引，或使用一种方法，而不是索引器。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 禁止显示此规则仅在仔细考虑对非标准的索引器的需求后的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示一种类型， `DayOfWeek03`，使用与该规则冲突的多维索引器。 索引器可以被视为一种转换，因此更恰当公开作为一种方法。 类型中重新设计了`RedesignedDayOfWeek03`以满足该规则。  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1043：将整型或字符串参数用于索引器](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)