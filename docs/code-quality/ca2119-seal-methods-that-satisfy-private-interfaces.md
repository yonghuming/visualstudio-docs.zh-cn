---
title: "CA2119：密封满足私有接口的方法 | Microsoft Docs"
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
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119：密封满足私有接口的方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|类别|Microsoft.Security|  
|是否重大更改|是|  
  
## 原因  
 可继承的公共类型为 `internal`（在 Visual Basic 中为 `Friend`）接口提供可重写的方法实现。  
  
## 规则说明  
 接口方法具有公共可访问性，不能通过该实现类型来更改。  内部接口会创建一个不应在定义该接口的程序集外部实现的协定。  使用 `virtual`（在 Visual Basic 中为 `Overridable`）修饰符实现内部接口的方法的公共类型允许程序集外部的派生类型重写该方法。  如果定义程序集中的第二个类型调用该方法，并期望创建一个纯内部协定，则当执行在外部程序集中重写的方法时，可能会对行为的安全性造成威胁。  这会产生安全漏洞。  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请使用下面的方法之一防止该方法在程序集外部被重写：  
  
-   使该声明类型成为 `sealed`（在 Visual Basic 中为 `NotInheritable`）。  
  
-   将声明类型的可访问性更改为 `internal`（在 Visual Basic 中为 `Friend`）。  
  
-   从该声明类型中移除所有公共构造函数。  
  
-   在不使用 `virtual` 修饰符的情况下实现该方法。  
  
-   显式实现该方法。  
  
## 何时禁止显示警告  
 经认真检查后，认定如果该方法在程序集外部被重写，并不存在可能被利用的安全问题，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示了一个违反该规则的类型 `BaseImplementation`。  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## 示例  
 下面的示例利用上面示例的虚方法实现。  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## 请参阅  
 [接口](/dotnet/csharp/programming-guide/interfaces/index)   
 [接口](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)