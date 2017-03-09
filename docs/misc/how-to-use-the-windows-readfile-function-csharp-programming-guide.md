---
title: "如何：使用 Windows ReadFile 函数（C# 编程指南） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile 函数 [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# 如何：使用 Windows ReadFile 函数（C# 编程指南）
下面的示例通过读取并显示一个文本文件来演示 Windows `ReadFile` 函数。  `ReadFile` 函数需要使用 `unsafe` 代码，因为它需要一个作为参数的指针。  
  
 传递到 `Read` 函数的字节数组是托管类型。  这意味着公共语言运行时 \(CLR\) 垃圾回收器可能会随意地对数组使用的内存进行重新定位。  为了防止出现这种情况，使用 [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) 来获取指向内存的指针并对它进行标记，以便垃圾回收器不会移动它。  在 `fixed` 块的末尾，内存将自动返回，以便能够通过垃圾回收移动。  
  
 此功能称为“声明式锁定”。  使用锁定，系统开销会非常小，除非在 `fixed` 块中发生垃圾回收（但此情况不太可能发生）。  但是，锁定会在全局垃圾回收运行过程中导致某些不利的副作用。  垃圾回收器压缩内存的能力在很大程度上受到锁定缓冲区的限制。  因此，应尽可能避免使用锁定。  
  
## 示例  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## 请参阅  
 [C\# 编程指南](/dotnet/csharp/programming-guide/index)   
 [C\# 参考](/dotnet/csharp/language-reference/index)   
 [不安全代码和指针](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [指针类型](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)