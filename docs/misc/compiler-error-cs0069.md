---
title: "编译器错误 CS0069 | Microsoft Docs"
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
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0069
接口中的事件不能具有 add 或 remove 访问器  
  
 不能在[接口](/dotnet/csharp/language-reference/keywords/interface)中定义某一事件的访问器函数。 有关详细信息，请参阅 [事件](/dotnet/csharp/programming-guide/events/index) 和 [接口](/dotnet/csharp/programming-guide/interfaces/index)。  
  
 以下示例生成 CS0069：  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```