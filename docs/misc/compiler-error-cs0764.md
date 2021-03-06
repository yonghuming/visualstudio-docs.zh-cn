---
title: "编译器错误 CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0764
两个分部方法声明必须都是不安全声明，或者两者都不能是不安全声明  
  
 分部方法由定义声明（签名）和可选的实现声明（主体）组成。 如果定义声明具有 `unsafe` 修饰符，则实现声明也必须具有该修饰符。 反之，如果实现声明具有 `unsafe` 修饰符，定义声明也必须具有该修饰符。  
  
### 更正此错误  
  
1.  假设定义声明是正确的，从实现声明添加或删除 `unsafe` 修饰符，以使之与定义声明匹配。  
  
## 示例  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## 请参阅  
 [分部类和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)