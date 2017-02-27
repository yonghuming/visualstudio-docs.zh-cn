---
title: "CA1802：在合适的位置使用文本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1802：在合适的位置使用文本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 某个字段被声明为 `static` 和 `readonly`（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 `Shared` 和 `ReadOnly`），并使用可在编译时计算的值初始化。  
  
## 规则说明  
 在调用声明类型的静态构造函数时，会在运行时计算 `static` `readonly` 字段的值。  如果在声明 `static` `readonly` 字段时未对其进行初始化，而且未显式声明静态构造函数，则编译器会发出一个静态构造函数来初始化该字段。  
  
 `const` 字段的值在编译时计算并将存储在元数据库中，与 `static` `readonly` 字段相比，这有助于提高运行时性能。  
  
 因为赋给目标字段的值可在编译时计算，所以，请将声明更改为 `const` 字段，以便该值在编译时（而非运行时）计算。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请将 `static` 和 `readonly` 修饰符替换为 `const` 修饰符。  
  
## 何时禁止显示警告  
 如果无需顾虑性能，可以安全地禁止显示此规则发出的警告，或者禁用此规则。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型 \(`UseReadOnly`\) 和一个满足该规则的类型 \(`UseConstant`\)。  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]