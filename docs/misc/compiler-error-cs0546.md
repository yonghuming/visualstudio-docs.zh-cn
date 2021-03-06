---
title: "编译器错误 CS0546 | Microsoft Docs"
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
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0546
“accessor”: 无法重写，因为“property”没有可重写的 set 访问器  
  
 试图对属性的访问器方法之一进行重写时失败，因为访问器不能重写。 以下情况下可能发生此错误：  
  
-   基类属性未声明为 [virtual](/dotnet/csharp/language-reference/keywords/virtual)。  
  
-   基类属性未声明你试图重写的 [get](/dotnet/csharp/language-reference/keywords/get) 或 [set](/dotnet/csharp/language-reference/keywords/set) 访问器。  
  
 如果不想重写基类属性，可以在派生类的属性前面使用 [new](/dotnet/csharp/language-reference/keywords/new) 关键字。  
  
 有关详细信息，请参阅[使用属性](/dotnet/csharp/programming-guide/classes-and-structs/using-properties)。  
  
## 示例  
 下面的示例生成 CS0546，因为基类没有为属性声明 set 访问器。  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## 请参阅  
 [属性](/dotnet/csharp/programming-guide/classes-and-structs/properties)