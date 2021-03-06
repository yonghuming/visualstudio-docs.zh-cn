---
title: "不能在匿名类型声明中使用类型字符 | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能在匿名类型声明中使用类型字符
声明匿名类型的实例时，不能在属性名称中使用类型字符。 属性的数据类型是从赋给它的值推断出来的。 例如，下面的声明无效。  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **错误 ID：**BC36560  
  
### 更正此错误  
  
-   从初始值设定项列表中删除类型字符。 如果需要，可以显式转换所赋的值，以便为属性建立所需的数据类型。  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## 请参阅  
 [匿名类型](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [如何：推断匿名类型声明中的属性名和类型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [隐式转换和显式转换](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)