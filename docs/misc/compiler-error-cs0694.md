---
title: "编译器错误 CS0694 | Microsoft Docs"
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
  - "CS0694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0694"
ms.assetid: 048615e4-4599-4726-b5db-55322ccc936f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0694
类型形参“identifier”与包含类型或方法同名  
  
 必须为类型形参使用不同名称，因为类型形参不能与包含该类型形参的类型或方法同名。  
  
## 示例  
 以下示例生成 CS0694。  
  
```  
// CS0694.cs // compile with: /target:library class C<C> {}   // CS0694  
```  
  
## 示例  
 除了涉及泛型类的以上示例，使用一种方法也可能发生此错误：  
  
```  
// CS0694_2.cs // compile with: /target:library class A { public void F<F>(F arg);   // CS0694 }  
```