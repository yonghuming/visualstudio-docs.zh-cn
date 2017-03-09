---
title: "编译器错误 CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0199
无法向静态只读字段“name”的字段传递 ref 或 out（在静态构造函数中除外）  
  
 一个 [readonly](/dotnet/csharp/language-reference/keywords/readonly) 变量必须与构造函数具有相同的 [静态](/dotnet/csharp/language-reference/keywords/static)用法，在此构造函数中你要将其作为 [ref](/dotnet/csharp/language-reference/keywords/ref) 或 [out](/dotnet/csharp/language-reference/keywords/out) 参数传递。 有关详细信息，请参阅[传递参数](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)。  
  
## 示例  
 以下示例生成 CS0199：  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```