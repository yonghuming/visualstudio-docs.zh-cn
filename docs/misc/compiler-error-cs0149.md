---
title: "编译器错误 CS0149 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0149"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0149"
ms.assetid: c3c0e48e-8dba-4ee6-86fd-cbb02c68255c
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0149
应输入方法名称  
  
 在创建[委托](/dotnet/csharp/language-reference/keywords/delegate)时，指定一个方法。 有关详细信息，请参阅[委托](/dotnet/csharp/programming-guide/delegates/index)。  
  
 以下示例生成 CS0149：  
  
```  
// CS0149.cs using System; delegate string MyDelegate(int i); class MyClass { // class member-field of the declared delegate type static MyDelegate dt; public static void Main() { dt = new MyDelegate(17.45);   // CS0149 // try the following line instead // dt = new MyDelegate(Func2); F(dt); } public static string Func2(int j) { Console.WriteLine(j); return j.ToString(); } public static void F(MyDelegate myFunc) { myFunc(8); } }  
```