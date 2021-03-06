---
title: "无法继承接口“&lt;interfacename1&gt;”，因为对于某些类型实参，所继承的接口“&lt;interfacename2&gt;”可能与接口“&lt;interfacename4&gt;”所继承的“&lt;interfacename3&gt;”相同。 | Microsoft Docs"
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
  - "vbc32122"
  - "bc32122"
helpviewer_keywords: 
  - "BC32122"
ms.assetid: 64a66ec7-0f5f-4804-a92b-9a6279fdfd6d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法继承接口“&lt;interfacename1&gt;”，因为对于某些类型实参，所继承的接口“&lt;interfacename2&gt;”可能与接口“&lt;interfacename4&gt;”所继承的“&lt;interfacename3&gt;”相同。
泛型接口继承自两个或多个泛型接口，对于某些类型实参的值，两个继承可能冲突。  
  
 以下语句可能会生成此错误。  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface interfaceY(Of w) Inherits interfaceA(Of w) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceX(Of t1), interfaceY(Of t2) End Interface  
```  
  
 如果构造或实现 `derivedInterface` 时同时向 `t1` 和 `t2` 提供相同类型，则它必须继承类型参数相同的两个版本的 `interfaceA`。 如果这样做，则在访问哪个版本方面存在歧义。  
  
 **错误 ID：**BC32122  
  
### 更正此错误  
  
-   更改提供给派生接口的类型实参之一，以避免冲突。  
  
     \- 或 \-  
  
-   删除 `Inherits` 语句中可能导致继承或实现冲突的接口之一。  
  
## 请参阅  
 [不在生成中：接口概述](http://msdn.microsoft.com/zh-cn/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface 语句](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [继承的基础知识](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits 语句](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)