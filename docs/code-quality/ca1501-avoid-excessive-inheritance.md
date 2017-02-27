---
title: "CA1501：避免过度继承 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1501：避免过度继承
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|类别|Microsoft.Maintainability|  
|是否重大更改|是|  
  
## 原因  
 类型在继承层次结构中的深度超过四级。  
  
## 规则说明  
 深度嵌套的类型层次结构可能很难遵循、理解和维护。  此规则将分析限制在同一模块内的层次结构。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请从继承层次结构中较浅的基类型派生类型，或者消除一些中间基类型。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告。  但是，代码可能会更难维护。  请注意，根据基类型的可见性，解决与该规则的冲突可能会造成重大更改。  例如，移除公共基类型就是一项重大更改。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]