---
title: "CA1014：用 CLSCompliantAttribute 标记程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014：用 CLSCompliantAttribute 标记程序集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 某程序集未应用 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 特性。  
  
## 规则说明  
 公共语言规范 \(CLS\) 定义了程序集在跨编程语言使用时必须符合的命名限制、数据类型和规则。  好的设计要求所有程序集用 <xref:System.CLSCompliantAttribute> 显式指示 CLS 符合性。  如果程序集没有该特性，该程序集就不符合 CLS。  
  
 符合 CLS 的程序集可能包含不符合的类型或类型成员。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将该特性添加到程序集。  不要将整个程序集标记为不符合，而应当确定哪些类型或类型成员不符合，并将这些元素标记为不符合。  如果可能，您应当为不符合的成员提供符合 CLS 的其他选择，使得尽可能多的用户可以访问您的程序集的所有功能。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  如果不想让程序集符合，请应用该特性，并将其值设置为 `false`。  
  
## 示例  
 下面的示例演示一个程序集，其 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 特性声明该程序集符合 CLS。  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## 请参阅  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)