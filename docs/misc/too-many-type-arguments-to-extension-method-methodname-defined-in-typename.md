---
title: "在“&lt;typeName&gt;”中定义的扩展方法“&lt;methodName&gt;”的类型实参过多 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36591"
  - "vbc36591"
helpviewer_keywords: 
  - "BC36591"
ms.assetid: 504c9b1f-f511-4198-8970-136d1a1bdafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在“&lt;typeName&gt;”中定义的扩展方法“&lt;methodName&gt;”的类型实参过多
用多于现有类型形参的类型实参调用了泛型扩展方法。  
  
 在调用泛型方法时，必须为此方法定义的每一个类型形参提供一个类型实参。  
  
 **错误 ID：**BC36591  
  
### 更正此错误  
  
-   从类型实参列表删除类型实参，使所调用泛型方法定义的每个类型形参都有一个类型实参。  
  
## 请参阅  
 [扩展方法](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [类型列表](/dotnet/visual-basic/language-reference/statements/type-list)