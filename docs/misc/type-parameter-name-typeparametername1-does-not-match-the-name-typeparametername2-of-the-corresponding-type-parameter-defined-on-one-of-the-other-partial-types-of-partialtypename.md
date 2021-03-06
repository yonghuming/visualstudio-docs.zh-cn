---
title: "类型形参名“&lt;typeparametername1&gt;”与某个其他分部类型“&lt;partialtypename&gt;”上定义的相应类型形参的名称“&lt;typeparametername2&gt;”不匹配 | Microsoft Docs"
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
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型形参名“&lt;typeparametername1&gt;”与某个其他分部类型“&lt;partialtypename&gt;”上定义的相应类型形参的名称“&lt;typeparametername2&gt;”不匹配
在多个分部声明中定义的泛型类或结构与类型形参规范冲突。  
  
 在多个分部声明中划分类或结构的定义时，编译器将该类型视为其所有分部声明的联合。 这不仅适用于成员，还适用于实现、继承和访问级别。  
  
 不能在泛型类或结构的定义中为任何类型形参指定多个名称。  
  
 **错误 ID:** BC30931  
  
### 更正此错误  
  
-   确定类型形参的名称，并在每个分部声明中使用相同的名称。  
  
## 请参阅  
 [分部](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Class 语句](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure 语句](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [不在生成中：类：对象的蓝图](http://msdn.microsoft.com/zh-cn/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [结构](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [类型列表](/dotnet/visual-basic/language-reference/statements/type-list)