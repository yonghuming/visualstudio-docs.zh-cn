---
title: "CA2230：对可变数量的参数使用 params | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230：对可变数量的参数使用 params
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|类别|Microsoft.Usage|  
|是否重大更改|是|  
  
## 原因  
 公共或受保护类型包含一个使用 `VarArgs` 调用约定的公共或受保护方法。  
  
## 规则说明  
 `VarArgs` 调用约定与采用个数可变的参数的特定方法定义一起使用。  使用 `VarArgs` 调用约定的方法不符合公共语言规范 \(CLS\)，因此可能无法被所有编程语言访问。  
  
 在 C\# 中，当方法的参数列表以 `__arglist` 关键字结尾时，使用 `VarArgs` 调用约定。  Visual Basic 不支持 `VarArgs` 调用约定，且 Visual C\+\+ 仅允许它在使用省略号 `...` 表示法的非托管代码中使用。  
  
## 如何解决冲突  
 要修复 C\# 中与该规则的冲突，请使用 [params](/dotnet/csharp/language-reference/keywords/params) 关键字来替代 `__arglist`。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示两个方法，其中一个与规则冲突，另一个满足规则。  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## 请参阅  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)