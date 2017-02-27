---
title: "CA1800：避免进行不必要的强制转换 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800：避免进行不必要的强制转换
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法对其参数或局部变量之一执行重复的强制转换。  要通过该规则进行全面分析，必须使用调试信息生成被测试的程序集，并且关联的程序数据库 \(.pdb\) 文件必须可用。  
  
## 规则说明  
 重复强制转换会降低性能，特别是在精简的迭代语句中执行强制转换时。  对于显式重复强制转换操作，将强制转换的结果存储在局部变量中，并使用局部变量来替代重复强制转换操作。  
  
 如果在执行实际的强制转换之前，使用 C\# `is` 运算符来测试强制转换是否将成功，请考虑转为测试 `as` 运算符的结果。  后者可以提供相同的功能，但不需要由 `is` 运算符执行的隐式强制转换操作。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请修改方法实现，以最大限度地减少强制转换操作的次数。  
  
## 何时禁止显示警告  
 如果无需顾虑性能，则可以安全地禁止显示此规则发出的警告，或者完全忽略此规则。  
  
## 示例  
 下面的示例演示一个使用 C\# `is` 运算符的与规则冲突的方法。  第二个方法将 `is` 运算符替换为针对 `as` 运算符的结果进行的测试（该测试将每个迭代的强制转换操作的次数从两次减少为一次），从而满足该规则。  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## 示例  
 下面的示例演示一个与规则冲突的方法 `start_Click`（多次重复执行显式强制转换）和一个满足规则的方法 `reset_Click`（将强制转换存储在局部变量中）。  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## 请参阅  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)