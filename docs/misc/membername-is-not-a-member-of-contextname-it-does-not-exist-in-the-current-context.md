---
title: "“&lt;成员名称&gt;”不是“&lt;上下文名称&gt;”的成员；它不存在于当前上下文中 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;成员名称&gt;”不是“&lt;上下文名称&gt;”的成员；它不存在于当前上下文中
已将不存在的成员名称分配到匿名类型声明中的属性。 在下面示例中，`.Prop1` 和 `.Prop2` 都是匿名类型的属性。 尝试将 `.Prop3` 分配到 `.Prop2` 会导致错误。  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **错误 ID：**BC36657  
  
### 更正此错误  
  
-   检查代码以确定哪些是你想要分配的。 变量名称可能拼写错误，或者，如果它是另一个对象的属性，可能需要限定。  
  
## 请参阅  
 [匿名类型](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [如何：推断匿名类型声明中的属性名和类型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)