---
title: "CA1708： 标识符应是多个用例不同 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda7936a1a701b1b51957a7038db496f70ddd9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708：标识符不应仅以大小写进行区分
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 形式的两种类型、 成员、 参数或完全限定的命名空间的名称相同时它们会转换为小写。  
  
## <a name="rule-description"></a>规则说明  
 不能仅通过大小写区分命名空间、类型、成员和参数的标识符，因为针对公共语言运行时的语言不需要区分大小写。 例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]是广泛使用的不区分大小写语言。  
  
 仅公开可见的成员上，将引发此规则。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 选择它与其他标识符的相比不区分大小写的方式都是唯一的名称。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。 库可能不能使用所有可用的语言中[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
## <a name="example-of-a-violation"></a>冲突的示例  
 下面的示例演示此规则的冲突。  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)