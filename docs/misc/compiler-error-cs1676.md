---
title: "编译器错误 CS1676 | Microsoft Docs"
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
  - "CS1676"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1676"
ms.assetid: 5ac83d98-5baa-49fd-b76a-d8ef0865b9dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1676
参数“number”必须使用“keyword”关键字进行声明  
  
 当匿名方法中的参数类型修饰符不同于你要将方法转换为的委托的声明中所用的参数类型修饰符时，将出现此错误。  
  
 以下示例生成 CS1676：  
  
```  
// CS1676.cs delegate void E(ref int i); class Errors { static void Main() { E e = delegate(out int i) { };   // CS1676 // To resolve, use the following line instead: // E e = delegate(ref int i) { }; } }  
```