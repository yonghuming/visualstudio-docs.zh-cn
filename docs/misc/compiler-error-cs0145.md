---
title: "编译器错误 CS0145 | Microsoft Docs"
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
  - "CS0145"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0145"
ms.assetid: e5f9a90f-1700-4e6a-8f82-23d0c0287b85
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0145
常量字段要求提供一个值  
  
 必须初始化 [const](/dotnet/csharp/language-reference/keywords/const) 变量。 有关更多信息，请参见[常量](/dotnet/csharp/programming-guide/classes-and-structs/constants)。  
  
 以下示例生成 CS0145：  
  
```  
// CS0145.cs class MyClass { const int i;   // CS0145 // try the following line instead // const int i = 0; public static void Main() { } }  
```