---
title: "可选参数不能声明为类型“&lt;type&gt;” | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 可选参数不能声明为类型“&lt;type&gt;”
可选参数不能具有结构的数据类型。  
  
 **错误 ID：**BC30423  
  
### 更正此错误  
  
1.  要向可选参数传递结构，请将参数声明为 `Object`。  
  
2.  在过程中使用 `CType` 将参数强制转换为该结构类型。  
  
## 请参阅  
 [结构和类](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [CType 函数](/dotnet/visual-basic/language-reference/functions/ctype-function)