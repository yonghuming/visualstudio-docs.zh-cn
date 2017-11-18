---
title: "CA1504： 检查令人误解的字段名 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d03c07b48b2cfbfc19fcb9aa2ac4353ddf87a8a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504：检查令人误解的字段名
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|类别|Microsoft.Maintainability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 实例字段的名称以"s_"或名称开头`static`(`Shared`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 以"m_"开头的字段。  
  
## <a name="rule-description"></a>规则说明  
 以"s_"开头的字段名是由多个用户的静态数据相关联。 同样，以"m_"开头的字段名是与实例 （成员） 的数据关联。 对于更易于维护的代码，名称应遵循通常使用的约定。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请使用相应的前缀重命名字段。 另外，还可以使该字段与当前后缀相符通过添加或删除`static`修饰符。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。