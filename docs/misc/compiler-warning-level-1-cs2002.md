---
title: "编译器警告（等级 1）CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 1）CS2002
多次指定源文件“file”  
  
 已多次将源文件名称传递到编译器。 你只能对编译器指定一次文件来生成输出文件。  
  
 此警告不能由 [\/nowarn](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) 选项禁止。  
  
 以下示例生成 CS2002：  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 若要生成该错误，请使用命令行编译示例：  
  
```  
csc CS2002.cs CS2002.cs  
```