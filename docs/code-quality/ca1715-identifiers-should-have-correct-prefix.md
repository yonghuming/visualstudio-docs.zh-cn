---
title: "CA1715：标识符应具有正确的前缀 | Microsoft Docs"
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
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1715：标识符应具有正确的前缀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|类别|Microsoft.Naming|  
|是否重大更改|是 \- 如果对接口引发。<br /><br /> 无间断 \- 如果是针对泛型类型参数引发的。|  
  
## 原因  
 外部可见的接口的名称不以大写的“I”开头。  
  
 \- 或 \-  
  
 外部可见的类型或方法上的泛型类型参数的名称不以大写的“T”开头。  
  
## 规则说明  
 按照约定，某些编程元素的名称以特定前缀开头。  
  
 接口名称应以大写字母“I”开头，后跟另一个大写字母。  该规则报告诸如“MyInterface”和“IsolatedInterface”的接口名称冲突。  
  
 泛型类型参数名称应以大写字母“T”开头，后面可跟另一个大写字母。  此规则报告泛型类型参数名称的冲突，例如“V”和“Type”。  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 重命名标识符，以便它使用正确的前缀。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 **下面的示例显示了一个未正确命名的接口。**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## 示例  
 **下面的示例通过在此接口前添加前缀“I”修复了上面的冲突。**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## 示例  
 **下面的示例显示了一个未正确命名的泛型类型参数。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## 示例  
 **下面的示例通过在此泛型类型参数前添加前缀“T”修复了上面的冲突。**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## 相关规则  
 [CA1722：标识符应采用正确的前缀](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)