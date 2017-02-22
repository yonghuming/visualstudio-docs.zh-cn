---
title: "CA1011：考虑将基类型作为参数传递 | Microsoft Docs"
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
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1011：考虑将基类型作为参数传递
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 某方法声明包含一个派生类型的形参，且该方法仅调用该参数的基类型的成员。  
  
## 规则说明  
 在方法声明中将基类型指定为参数时，可以将派生自基类型的任何类型作为相应的参数传递给方法。  在方法体中使用该变量时，所执行的特定方法取决于该变量的类型。  如果不需要派生类型提供的其他功能，则使用基类型将使方法可以得到更广泛的使用。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将参数的类型更改为其基类型。  
  
## 何时禁止显示警告  
 可以安全地禁止显示此规则发出的警告  
  
-   如果该方法需要由派生的类型提供的特定功能  
  
     \- 或 \-  
  
-   强制要求只有该派生类型或另一个派生类型传递给方法。  
  
 在这些情况下，代码将更为可靠，因为编译器和运行时会提供强类型检查。  
  
## 示例  
 下面的示例演示与该规则冲突的方法 `ManipulateFileStream`，此方法只能与 <xref:System.IO.FileStream> 对象一起使用。  第二个方法 `ManipulateAnyStream` 将 <xref:System.IO.FileStream> 参数替换为 <xref:System.IO.Stream>，从而满足该规则。  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## 相关规则  
 [CA1059：成员不应公开某些具体类型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)