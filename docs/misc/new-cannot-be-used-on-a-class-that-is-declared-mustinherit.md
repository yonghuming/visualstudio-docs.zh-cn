---
title: "“New”不能在声明为“MustInherit”的类上使用 | Microsoft Docs"
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
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “New”不能在声明为“MustInherit”的类上使用
不能直接实例化 `MustInherit` 类，因此不可在 `MustInherit` 类上使用 `New` 运算符。 虽然变量和值的编译时类型可以为 `MustInherit`，但此类变量和值必须为 null 值或包含对派生自 `MustInherit` 类型的常规类的实例的引用。  
  
 **错误 ID：**BC30569  
  
### 更正此错误  
  
-   删除 `New` 运算符。  
  
## 请参阅  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [New 运算符](/dotnet/visual-basic/language-reference/operators/new-operator)