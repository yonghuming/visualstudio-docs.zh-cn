---
title: "编译器错误 CS0743 | Microsoft Docs"
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
  - "CS0743"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0743"
ms.assetid: 0dc8040a-a12f-4da6-9ed0-c0284905ee83
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0743
应为上下文关键字 "on"  
  
 `join` 子句的模式是 `join`...`in`...`on`...`equals`，如本示例所示：  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### 更正此错误  
  
1.  将 `on` 关键字添加到 `join` 子句中。  
  
## 示例  
 下面的代码生成 CS0743：  
  
```  
// cs0743.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 x equals y // CS0743 select x; return 1; } }  
```  
  
## 请参阅  
 [LINQ 查询表达式](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [join 子句](/dotnet/csharp/language-reference/keywords/join-clause)