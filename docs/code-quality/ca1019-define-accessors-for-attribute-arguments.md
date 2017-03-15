---
title: "CA1019：定义特性参数的访问器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019：定义特性参数的访问器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## 原因  
 在其构造函数中，特性定义了没有相应属性的参数。  
  
## 规则说明  
 特性可以定义强制实参，在对目标应用该特性时必须指定这些实参。  这些实参也称为位置实参，因为它们将作为位置形参提供给特性构造函数。  对于每一个强制变量，特性还必须提供一个相应的只读属性，以便可以在执行时检索该变量的值。  该规则将检查您是否为每一个构造函数形参定义了相应的属性。  
  
 特性还可以定义可选实参，可选实参也称为命名实参。  这些变量按名称提供给特性构造函数，并且必须具有相应的读\/写属性。  
  
 对于强制变量和可选变量，相应的属性和构造函数参数应使用相同的名称，但大小写形式不同。  属性使用 Pascal 大小写形式，参数使用 Camel 大小写形式。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请为每一个不具有只读属性的构造函数参数添加只读属性。  
  
## 何时禁止显示警告  
 如果不希望强制参数的值可供检索，则可以禁止显示与该规则有关的警告。  
  
## 自定义特性示例  
  
### 说明  
 下面的示例演示两个定义强制（位置）参数的特性。  第一个特性实现的定义是错误的。  第二个实现是正确的。  
  
### 代码  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## 位置和命名参数  
  
### 说明  
 位置和命名参数可以让库的使用者清楚哪些参数对于特性是强制的，哪些参数是可选的。  
  
 下面的示例演示具有位置和命名参数的特性的实现。  
  
### 代码  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### 注释  
 下面的示例演示如何将自定义特性应用于两个属性。  
  
### 代码  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## 相关规则  
 [CA1813：避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## 请参阅  
 [特性](../Topic/Attributes1.md)