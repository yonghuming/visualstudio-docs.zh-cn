---
title: "“AddressOf”表达式无法转换为“&lt;typename&gt;”，因为类型“&lt;typename&gt;”被声明为“MustInherit”，无法创建。 | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “AddressOf”表达式无法转换为“&lt;typename&gt;”，因为类型“&lt;typename&gt;”被声明为“MustInherit”，无法创建。
一条语句尝试将 `AddressOf` 表达式转换为某个类型，此类型只能是基类，并且不能用于创建实例。  
  
 `AddressOf` 运算符创建引用特定过程的过程委托实例。  
  
 **错误 ID：**BC30939  
  
### 更正此错误  
  
-   将 `AddressOf` 表达式分配到特定委托类型。  
  
## 请参阅  
 [AddressOf 运算符](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [不在生成中：委托和 AddressOf 运算符](http://msdn.microsoft.com/zh-cn/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [委托](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)