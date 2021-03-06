---
title: "编译器错误 CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0837
“is”或“as”运算符的第一个操作数不能是 lambda 表达式或匿名方法。  
  
 Lambda 表达式和匿名方法不能在 [is](/dotnet/csharp/language-reference/keywords/is) 或 [as](/dotnet/csharp/language-reference/keywords/as) 的左侧使用。  
  
### 更正此错误  
  
-   如果错误涉及 `is` 运算符，请记住，`is` 会采用一个值和一种类型，并会告诉你是否可以通过引用、装箱或取消装箱转换将该值转换为该类型。 由于 lambda 不是值并且没有引用、装箱或取消装箱转换，因此 lambda 不适用于 `is`。  
  
-   如果代码误用了 `as`，则更正方法可能是将它更改为强制转换。  
  
## 示例  
 下面的示例生成 CS0837：  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```