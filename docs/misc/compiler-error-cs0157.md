---
title: "编译器错误 CS0157 | Microsoft Docs"
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
  - "CS0157"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0157"
ms.assetid: a5d9d506-81f8-47dd-85b6-85f8170bcbef
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0157
控制不能离开 finally 子句主体  
  
 [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally) 子句中的所有语句都必须执行。 有关详细信息，请参阅[异常处理语句](/dotnet/csharp/language-reference/keywords/exception-handling-statements)和[异常和异常处理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)。  
  
 下面的示例生成 CS0157：  
  
```  
// CS0157.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } finally { return;   // CS0157, cannot leave finally clause } } } }  
```