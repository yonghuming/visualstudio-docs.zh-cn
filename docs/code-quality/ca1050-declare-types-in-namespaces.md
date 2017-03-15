---
title: "CA1050：在命名空间中声明类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1050：在命名空间中声明类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 在命名的命名空间范围之外定义了公共或受保护类型。  
  
## 规则说明  
 应在命名空间内声明类型以避免名称冲突，并作为一种在对象层次结构中组织相关类型的方式。  位于任何命名的命名空间之外的类型属于全局命名空间，全局命名空间无法在代码中引用。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将类型置于命名空间中。  
  
## 何时禁止显示警告  
 尽管永远无需禁止显示此规则发出的警告，但是如果该程序集永远都不会与其他程序集一起使用，则可以安全地禁止显示警告。  
  
## 示例  
 下面的示例演示一个库，该库包含一个错误地在命名空间外进行声明的类型，以及一个在命名空间内声明的同名类型。  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## 示例  
 下面的应用程序使用前面定义的库。  请注意，当名称 `Test` 未使用命名空间进行限定时，会创建在命名空间外声明的类型。  另外请注意，若要在 `Goodspace` 中访问 `Test` 类型，命名空间名称是必需的。  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]