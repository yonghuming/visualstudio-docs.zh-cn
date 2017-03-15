---
title: "CA1047：不要在密封类型中声明受保护的成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1047：不要在密封类型中声明受保护的成员
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 公共类型为 `sealed`（在 Visual Basic 中为 `NotInheritable`），并且声明了受保护的成员或受保护的嵌套类型。  该规则不报告 <xref:System.Object.Finalize%2A> 方法的冲突，该方法必须遵循此模式。  
  
## 规则说明  
 类型声明受保护的成员，使继承类型可以访问或重写该成员。  按照定义，不能从密封类型继承，意味着不能调用密封类型上受保护的方法。  
  
 C\# 编译器为此错误发出警告。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将成员的访问级别改为私有，或使类型可继承。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  使类型保持当前状态可能引发维护问题，不会带来任何好处。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]