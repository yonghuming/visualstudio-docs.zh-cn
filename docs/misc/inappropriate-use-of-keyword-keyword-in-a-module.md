---
title: "模块中不恰当地使用了 &lt;keyword&gt; 关键字 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模块中不恰当地使用了 &lt;keyword&gt; 关键字
模块没有实例、支持继承或实现接口。 因此，以下关键字不适用于模块声明：  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 [Module 语句](/dotnet/visual-basic/language-reference/statements/module-statement)中仅支持 [Public](/dotnet/visual-basic/language-reference/modifiers/public) 和 [Friend](/dotnet/visual-basic/language-reference/modifiers/friend) 关键字。  
  
 此外，不能在模块的语句块中使用 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) 语句或 [Inherits 语句](/dotnet/visual-basic/language-reference/statements/inherits-statement)。  
  
 默认情况下，此消息是一个警告。 有关如何隐藏警告或将警告视为错误的详细信息，请参阅[在 Visual Basic 中配置警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
 **错误 ID：**BC42028  
  
### 更正此错误  
  
-   如果你想将此编程元素作为模块，请在其声明中仅使用 `Public` 或 `Friend` 关键字。 默认情况下，如果不指定模块的访问级别，则它将使用 `Friend`。  
  
-   如果你想要创建此编程元素的实例，则将其声明为类。 然后可以使用适用于类声明的关键字。  
  
## 请参阅  
 [Class 语句](/dotnet/visual-basic/language-reference/statements/class-statement)