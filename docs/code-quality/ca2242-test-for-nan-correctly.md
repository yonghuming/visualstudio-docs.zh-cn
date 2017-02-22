---
title: "CA2242：正确测试 NaN | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2242：正确测试 NaN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TestForNaNCorrectly|  
|CheckId|CA2242|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 表达式针对 <xref:System.Single.Nan?displayProperty=fullName> 或 <xref:System.Double.Nan?displayProperty=fullName> 测试某个值。  
  
## 规则说明  
 当未定义算术运算时，<xref:System.Double.NaN?displayProperty=fullName> 表示非数字结果。  测试一个值与 <xref:System.Double.NaN?displayProperty=fullName> 之间的相等关系的任何表达式始终返回 `false`。  测试一个值与 <xref:System.Double.NaN?displayProperty=fullName> 之间的不等关系的任何表达式始终返回 `true`。  
  
## 如何解决冲突  
 若要修复与此规则的冲突并准确确定某个值是否表示 <xref:System.Double.NaN?displayProperty=fullName>，请使用 <xref:System.Single.IsNan%2A?displayProperty=fullName> 或 <xref:System.Double.IsNan%2A?displayProperty=fullName> 来测试值。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示针对 <xref:System.Double.NaN?displayProperty=fullName> 对某个值进行不正确测试的两个表达式，以及一个正确使用 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 测试该值的表达式。  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]