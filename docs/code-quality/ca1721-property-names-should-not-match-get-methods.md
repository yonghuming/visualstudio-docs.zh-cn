---
title: "CA1721： 属性名不应与 get 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91a280093d269797daa019b727bf2020462a0808
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721：属性名不应与 get 方法冲突
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护成员的名称以 Get，否则匹配公共或受保护的属性的名称。 例如，包含名为 GetColor 以及名为颜色的属性的方法的类型与该规则冲突。  
  
## <a name="rule-description"></a>规则说明  
 Get 方法和属性应具有明确表示其功能的名称。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这可减少所需了解新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员的时间。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 更改名称，以便与前缀为 Get 方法的名称不匹配。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
> [!NOTE]
>  如果 Get 方法由实现 iextenderprovider 接口接口可能排除此警告。  
  
## <a name="example"></a>示例  
 下面的示例包含的方法和违反了此规则的属性。  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)