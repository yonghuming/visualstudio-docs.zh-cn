---
title: "CA1819：属性不应返回数组 | Microsoft Docs"
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
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1819：属性不应返回数组
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|类别|Microsoft.Performance|  
|是否重大更改|是|  
  
## 原因  
 公共类型中的公共或受保护属性返回一个数组。  
  
## 规则说明  
 即使属性是只读的，该属性返回的数组也不是写保护的。  若要使数组不会被更改，属性必须返回数组的副本。  通常，用户不能理解调用这种属性的负面性能影响。  特别是，他们可能将该属性用作索引属性。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将属性更改为方法，或将属性更改为返回一个集合。  
  
## 何时禁止显示警告  
 特性可以包含返回数组的属性，但不能包含返回集合的属性。  可以禁止显示从 [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True) 类派生的特性的属性所引发的警告。  否则，不要禁止显示此规则发出的警告。  
  
## 冲突的示例  
  
### 说明  
 下面的示例演示一个与该规则冲突的属性。  
  
### 代码  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### 注释  
 若要修复与该规则的冲突，请将属性更改为方法，或将属性更改为返回一个集合而不是数组。  
  
## 将属性更改为方法的示例  
  
### 说明  
 下面的示例通过将属性更改为方法来修复冲突。  
  
### 代码  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## 返回集合的示例。  
  
### 说明  
 下面的示例通过以下方法修复冲突：将属性更改为返回一个  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### 代码  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## 允许用户修改属性  
  
### 说明  
 您可能希望允许类的使用者修改属性。  下面的示例演示一个与该规则冲突的读\/写属性。  
  
### 代码  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### 注释  
 下面的示例通过将属性更改为返回一个 <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName> 来修复冲突。  
  
### 代码  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## 相关规则  
 [CA1024：在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md)