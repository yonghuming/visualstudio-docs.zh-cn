---
title: "不能将属性访问器声明为“&lt;关键字&gt;” | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能将属性访问器声明为“&lt;关键字&gt;”
一个 `Get` 或 `Set` 过程声明中包含一个关键字，它在属性过程上不是有效的。  
  
 [Get 语句](/dotnet/visual-basic/language-reference/statements/get-statement) 和 [Set 语句](/dotnet/visual-basic/language-reference/statements/set-statement) 只允许访问修饰符（`Public`、`Protected`、`Friend`、`Protected Friend`、`Private`）。  
  
 **错误 ID：**BC31099  
  
### 更正此错误  
  
-   将无效的关键字从 `Get` 或 `Set` 语句中删除。  
  
## 请参阅  
 [Property 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)