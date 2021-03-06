---
title: "从类型参数约束“&lt;typeparameter1&gt;”获得的间接约束“&lt;constraint1&gt;”与从类型参数约束“&lt;typeparameter2&gt;”获得的间接约束“&lt;constraint2&gt;”冲突 | Microsoft Docs"
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
  - "bc32109"
  - "vbc32109"
helpviewer_keywords: 
  - "BC32109"
ms.assetid: 37abd3b4-25dc-4959-8617-ce93a02bbf47
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 从类型参数约束“&lt;typeparameter1&gt;”获得的间接约束“&lt;constraint1&gt;”与从类型参数约束“&lt;typeparameter2&gt;”获得的间接约束“&lt;constraint2&gt;”冲突
使用因间接约束的组合而导致发生冲突的约束声明了一个泛型类型。  
  
 以下语句可能会生成此错误。  
  
```  
Public Class testClass(Of t1 As {t2, t3}, t2 As Structure, t3 As Class)  
```  
  
 间接约束 `Structure` 和 `Class` 导致类型参数 `t1` 冲突，原因是 `Structure` 约束要求相应的类型变量为值类型，而 `Class` 要求类型变量为引用类型。  
  
 **错误 ID：**BC32109  
  
### 更正此错误  
  
-   更改类型形参约束以避免约束冲突。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [类型列表](/dotnet/visual-basic/language-reference/statements/type-list)   
 [结构 \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [类 \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [值类型和引用类型](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)