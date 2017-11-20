---
title: "CA1059： 成员不应公开某些具体类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5b8b4a50ce23a7ed50f2e608334f9b438a0b090
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059：成员不应公开某些具体类型
|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见成员是某些具体类型或公开某些具体类型的通过其参数之一或返回值。 目前，此规则将报告以下的具体类型的风险：  
  
-   从派生的类型<xref:System.Xml.XmlNode?displayProperty=fullName>。  
  
## <a name="rule-description"></a>规则说明  
 具体类型是指具有一个完整实现因此可以实例化的类型。 若要允许的成员可以得到广泛使用，使用建议的接口来替换具体类型。 这样，要接受实现接口的任何类型或实现接口的类型的地方使用的成员。  
  
 下表列出了目标的具体类型和它们的建议替换项。  
  
|具体的类型|Replacement|  
|-------------------|-----------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>。<br /><br /> 使用该接口将分离从 XML 数据源的特定实现的成员。|  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将具体的类型更改为建议的接口。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的消息，如果提供的具体类型的特定功能是必需的。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1011：考虑将基类型作为参数传递](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)