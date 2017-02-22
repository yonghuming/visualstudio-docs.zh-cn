---
title: "CA1061：不要隐藏基类方法 | Microsoft Docs"
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
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061：不要隐藏基类方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 派生类型声明一个与它的某个基方法具有相同名称和相同参数数目的方法；一个或多个参数是基方法中对应参数的基类型；任何其余参数的类型都与基方法中的对应参数完全相同。  
  
## 规则说明  
 如果派生方法的参数签名只是在类型方面有所不同，而且与基方法的参数签名中的对应类型相比，这些类型的派生方式更弱，则基类型中的方法将被派生类型中的同名方法隐藏。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请移除或重命名该方法，或者更改参数签名，使该方法不隐藏基方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示一个与该规则冲突的方法。  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]