---
title: "CA1505： 避免编写无法维护的代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3f31e213d621b64143f17735874238432118fe57
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505：避免编写无法维护的代码
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|CheckId|CA1505|  
|类别|Microsoft.Maintainability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 类型或方法具有较低的可维护性索引值。  
  
## <a name="rule-description"></a>规则说明  
 通过使用以下度量值来计算的可维护性索引： 代码、 程序卷和圈复杂度的行。 程序卷是了解类型或方法的运算符和操作数在代码中的数量为基础的难易程度的度量值。 圈复杂度是复杂性的一种结构化的类型或方法。 你可以了解有关在代码度量[测量复杂性和托管代码可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)。  
  
 低的可维护性索引指示类型或方法可能难以维护，并且会重新设计的良好候选。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要解决此冲突，重新设计的类型或方法，并尝试将它拆分为较小且更集中的类型或方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果类型或方法仍被视为可维护，尽管其尺寸大或者无法拆分的类型或方法中排除此警告。  
  
## <a name="see-also"></a>另请参阅  
 [可维护性警告](../code-quality/maintainability-warnings.md)   
 [测量托管代码的复杂性和可维护性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)