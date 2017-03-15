---
title: "CA1806：不要忽略方法结果 | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806：不要忽略方法结果
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|类别|Microsoft.Usage|  
|是否重大更改|否|  
  
## 原因  
 出现该警告的原因可能有多个：  
  
-   创建了新对象，但从未使用它。  
  
-   调用了创建并返回新字符串的方法，但从未使用此新字符串。  
  
-   COM 或 P\/Invoke 方法返回的 HRESULT 或错误代码从未使用过。  规则说明  
  
 创建不必要的对象以及与未使用的对象相关的垃圾回收会导致性能下降。  
  
 字符串是不可变的，诸如 String.ToUpper 之类的方法返回字符串的新实例，而不是在调用方法中修改字符串实例。  
  
 如果忽略 HRESULT 或错误代码，可能会导致在出错或资源不足的情况下出现意外行为。  
  
## 如何解决冲突  
 如果方法 A 创建了 B 对象的一个新实例，但该实例从未使用过，请将该实例作为参数传递给其他方法或将该实例赋给一个变量。  如果没有必要创建此对象，请移除它。\- 或 \-  
  
 如果方法 A 调用了方法 B，但并未使用方法 B 返回的新字符串实例。  请将此实例作为参数传递给其他方法并将此实例赋给一个变量。  或者，如果没有必要进行此调用，请移除此调用。  
  
 \- 或 \-  
  
 如果方法 A 调用了方法 B，但并未使用该方法返回的 HRESULT 或错误代码。  请在条件语句中使用此结果，将此结果赋给一个变量，或将其作为参数传递给其他方法。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告，除非创建对象的行为有特定的用途。  
  
## 示例  
 下面的示例演示一个忽略了调用 String.Trim 得到的结果的类。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## 示例  
 下面的示例通过将对一个变量调用 String.Trim 所得到的结果赋回此变量，修复了前面的冲突。  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## 示例  
 下面的示例显示了一个方法，此方法不使用其创建的一个对象。  
  
> [!NOTE]
>  此冲突在 Visual Basic 中无法重现。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## 示例  
 下面的示例通过移除不必要的对象创建操作修复了前面的冲突。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## 示例  
 下面的示例演示一个忽略了本机方法 GetShortPathName 返回的错误代码的方法。  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## 示例  
 下面的示例通过在调用失败时检查错误代码并引发异常修复了前面的冲突。  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]