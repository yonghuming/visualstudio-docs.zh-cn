---
title: "编译器错误 CS0542 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0542
“用户定义类型”: 成员名称不能与它们的封闭类型相同  
  
 类或结构的成员不能与类或结构同名，除非该成员是一个构造函数。  
  
 下面的示例生成 CS0542:  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 如果无意中将返回类型放在构造函数中（实际上会使其成为普通方法），则可能导致此错误。 下面的示例将生成 CS0542，因为 `F` 是一种方法，不是构造函数，因为它具有返回类型：  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 如果类命名为“Item”，并且具有一个声明为 `this` 的索引器 ，则可能出现此错误。 默认索引器在发出的代码中被命名为“Item”，从而导致冲突。  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```