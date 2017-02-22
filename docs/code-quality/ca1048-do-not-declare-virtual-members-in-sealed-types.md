---
title: "CA1048：不要在密封类型中声明虚拟成员 | Microsoft Docs"
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
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1048：不要在密封类型中声明虚拟成员
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某公共类型是密封的，并且声明了既 `virtual`（在 Visual Basic 中为 `Overridable`）又非 final 的方法。  该规则不报告委托类型的冲突，委托类型必须遵循此模式。  
  
## 规则说明  
 类型将方法声明为虚方法，使继承类型可以重写虚方法的实现。  根据定义，不能从密封类型继承，这使得密封类型上的虚方法没有意义。  
  
 Visual Basic .NET 和 C\# 编译器不允许类型与该规则冲突。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使方法成为非虚方法，或使类型可继承。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  使类型保持当前状态可能引发维护问题，不会带来任何好处。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]