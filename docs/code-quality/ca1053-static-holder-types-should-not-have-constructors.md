---
title: "CA1053：静态容器类型不应具有构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1053：静态容器类型不应具有构造函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 公共或嵌套公共类型只声明了静态成员，但具有公共或受保护的默认构造函数。  
  
## 规则说明  
 由于调用静态成员不需要类型的示例，因此没必要使用构造函数。  此外，由于类型没有非静态成员，即使创建实例也无法提供对类型的任何成员的访问。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请移除默认构造函数或将其设为私有成员。  
  
> [!NOTE]
>  如果类型没有定义任何构造函数，某些编译器会自动创建公共默认构造函数。  如果您的类型属于这种情况，请添加一个私有默认构造函数以消除此冲突。  
  
## 何时禁止显示警告  
 不要禁止显示此规则发出的警告。  存在构造函数表示该类型不是静态类型。  
  
## 示例  
 下面的示例演示一个与该规则冲突的类型。  请注意，在源代码中没有任何默认构造函数。  将此代码编译为程序集时，C\# 编译器将插入默认构造函数，这会与该规则冲突。  要更正此问题，请声明一个私有构造函数。  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]