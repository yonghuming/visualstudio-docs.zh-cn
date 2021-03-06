---
title: "“&lt;partialtypename&gt;”的指定访问“&lt;accesslevel1&gt;”与在它的其他分部类型之一上指定的访问“&lt;accesslevel2&gt;”不匹配 | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;partialtypename&gt;”的指定访问“&lt;accesslevel1&gt;”与在它的其他分部类型之一上指定的访问“&lt;accesslevel2&gt;”不匹配
在多个分部声明中使用冲突的访问级别规范定义了某个类或结构。  
  
 在多个分部声明中划分类或结构的定义时，编译器将该类型视为其所有分部声明的联合。 这不仅适用于成员，还适用于实现、继承和访问级别。  
  
 不能在类或结构的定义中混合访问级别。 即使是组合 `Protected Friend`，也只有当相同声明语句中关键字连续时才允许使用。  
  
 **错误 ID：**BC30925  
  
### 更正此错误  
  
-   确定类应有的访问级别，并删除任何有冲突的访问级别规范。  
  
## 请参阅  
 [分部](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Visual Basic 中的访问级别](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Class 语句](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure 语句](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [不在生成中：类：对象的蓝图](http://msdn.microsoft.com/zh-cn/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [结构](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)