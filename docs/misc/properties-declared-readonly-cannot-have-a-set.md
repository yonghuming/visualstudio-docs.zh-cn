---
title: "声明为“ReadOnly”的属性不能有“Set” | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 声明为“ReadOnly”的属性不能有“Set”
`Set` 过程写入属性的值。 不能写入 `ReadOnly` 属性。  
  
 **错误 ID：**BC30022  
  
### 更正此错误  
  
-   删除 `Property` 语句中的 `ReadOnly` 关键字，或者删除属性正文中的 `Set` 过程。  
  
## 请参阅  
 [Property 语句](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set 语句](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)