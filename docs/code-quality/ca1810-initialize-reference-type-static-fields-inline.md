---
title: "CA1810：以内联方式初始化引用类型的静态字段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1810：以内联方式初始化引用类型的静态字段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 某引用类型声明了显式静态构造函数。  
  
## 规则说明  
 当一个类型声明显式静态构造函数时，实时 \(JIT\) 编译器会向该类型的每个静态方法和实例构造函数中添加一项检查，以确保之前已调用该静态构造函数。  访问任何静态成员或创建了类型实例时，都会触发静态初始化。  不过，如果您声明但未使用一个在初始化更改全局状态时非常重要的类型变量，则不会触发静态初始化。  
  
 如果已内联初始化所有静态数据，而未声明显式静态构造函数，则 Microsoft 中间语言 \(MSIL\) 编译器将 `beforefieldinit` 标记和隐式静态构造函数（该构造函数会初始化静态数据）添加到 MSIL 类型定义中。  当 JIT 编译器遇到 `beforefieldinit` 标记时，在大多数情况下，不会添加静态构造函数检查。  静态初始化将保证在访问任何静态字段之前的某个时刻发生，但不会在调用静态方法或实例构造函数前发生。  请注意，声明类型的变量后会随时发生静态初始化。  
  
 静态构造函数检查会降低性能。  通常，静态构造函数仅用于初始化静态字段，此时，只需确保静态初始化在第一次访问静态字段之前发生。  `beforefieldinit` 行为对这些类型和大多数其他类型是适当的。  仅在静态初始化影响全局状态且下列条件之一成立时不适当：  
  
-   对全局状态的影响将耗费大量资源，如果不使用该类型则无需这样做。  
  
-   无需访问该类型的任何静态字段，即可访问全局状态影响。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请在声明它时初始化所有静态数据并移除静态构造函数。  
  
## 何时禁止显示警告  
 如果无需考虑性能问题，或者如果静态初始化造成的全局状态更改耗费大量资源，或者必须保证在调用类型的静态方法或创建类型实例前更改全局状态，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的类型 `StaticConstructor` 以及使用内联初始化替换静态构造函数以满足该规则的类型 `NoStaticConstructor`。  
  
 [!CODE [FxCop.Performance.RefTypeStaticCtor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor#1)]  
  
 请注意，在 `NoStaticConstructor` 类的 MSIL 定义中添加了 `beforefieldinit` 标记。  
  
  **.class public auto ansi StaticConstructor**  
 **扩展了 \[mscorlib\]System.Object**  
**{**  
**} \/\/ 类 StaticConstructor 结束**  
**.class public auto ansi beforefieldinit NoStaticConstructor**  
 **扩展了 \[mscorlib\]System.Object**  
**{**  
**} \/\/ 类 NoStaticConstructor 结束**   
## 相关规则  
 [CA2207：以内联方式初始化值类型的静态字段](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)