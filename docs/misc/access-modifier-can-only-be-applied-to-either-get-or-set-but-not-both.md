---
title: "访问修饰符只能用于“Get”或者“Set”，但不能同时用于这二者 | Microsoft Docs"
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
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 访问修饰符只能用于“Get”或者“Set”，但不能同时用于这二者
属性声明在 [Property 语句](/dotnet/visual-basic/language-reference/statements/property-statement)、[Get 语句](/dotnet/visual-basic/language-reference/statements/get-statement) 和 [Set 语句](/dotnet/visual-basic/language-reference/statements/set-statement) 中都指定了访问级别。  
  
 你始终可以为该属性指定访问级别。 此外，还可以至多为其一个属性过程（`Get` 或 `Set`）指定不同的访问级别，条件是该访问级别比属性访问级别限制性更强。 无法为两个属性过程指定访问级别。  
  
 **错误 ID：**BC31101  
  
### 更正此错误  
  
-   从 `Get` 语句或 `Set` 语句中删除访问修饰符。  
  
## 请参阅  
 [Property 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)