---
title: "编译器错误 CS1012 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1012
字符文本中的字符太多  
  
 尝试用多个字符初始化 [“char”](/dotnet/csharp/language-reference/keywords/char)常量。  
  
 在执行数据绑定时，也会发生 CS1012。 例如，下面行将发生错误：  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 改为尝试使用以下行：  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 以下示例生成 CS1012：  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```