---
title: "编译器错误 CS0716 | Microsoft Docs"
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
  - "CS0716"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0716"
ms.assetid: 806d25ef-f8a7-4c94-823e-e07904defcf4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0716
无法转换为静态类型“type”  
  
 如果你的代码使用强制转换来转换为静态类型，则会发生此错误。 由于对象不能是静态类型的实例，因此强制转换为静态类型并没有任何意义。  
  
## 示例  
 下面的示例生成 CS0716：  
  
```  
// CS0716.cs public static class SC { static void F() { } } public class Test { public static void Main() { object o = new object(); System.Console.WriteLine((SC)o);  // CS0716 } }  
```