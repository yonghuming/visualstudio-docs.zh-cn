---
title: "编译器警告（等级 1）CS1570 | Microsoft Docs"
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
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器警告（等级 1）CS1570
“construct”上的 XML 注释出现 XML 格式错误 —“reason”  
  
 当使用 [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) 时，源代码中的任何注释必须为 XML 格式。 XML 标记的任何错误将生成 CS1570。 例如:  
  
-   如果要传递一个字符串到 **cref**，例如，在[\<异常\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md)标记中，字符串必须括在双引号内。  
  
-   如果正在使用一个标记（如[\<另请参阅\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md)），其中不包含结束标记，则必须在右尖括号的前面指定一个正斜杠。  
  
-   如果你需要在说明文本使用大于或小于符号，你需要用 **&gt;** 或 **&lt;** 来表示它们。  
  
-   [\<包括\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md)标记上的文件或路径特性缺失或格式不正确。  
  
 以下示例生成 CS1570：  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```