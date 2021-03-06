---
title: "编译器错误 CS1601 | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1601
方法或委托参数不能是“type”类型  
  
 .NET Framework 类库中的一些类型，例如 <xref:System.TypedReference>、<xref:System.RuntimeArgumentHandle> 和 <xref:System.ArgIterator> 不能用作 [ref](/dotnet/csharp/language-reference/keywords/ref) 或 [out](/dotnet/csharp/language-reference/keywords/out) 参数，因为它们有可能会被用来执行不安全的操作。  
  
 下面的示例生成 CS1601：  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```