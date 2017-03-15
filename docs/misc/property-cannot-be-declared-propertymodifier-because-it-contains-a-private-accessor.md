---
title: "属性包含“Private”访问器，因此不能声明为“&lt;propertymodifier&gt;”。 | Microsoft Docs"
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
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性包含“Private”访问器，因此不能声明为“&lt;propertymodifier&gt;”。
具有 `Private` 属性过程（`Get` 或 `Set`）的属性被标记为 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)。  
  
 如果基类属性或过程声明为 [Private](/dotnet/visual-basic/language-reference/modifiers/private)，则派生类无法访问此属性或过程，因而不能重写它。 因此，不能结合使用 `Private` 和 `Overridable`。 这不仅适用于属性自身，也适用于单个属性过程。  
  
 **错误 ID：**BC31108  
  
### 更正此错误  
  
-   从 [Property 语句](/dotnet/visual-basic/language-reference/statements/property-statement) 删除 `Overridable` 关键字，或从 [Get 语句](/dotnet/visual-basic/language-reference/statements/get-statement) 或 [Set 语句](/dotnet/visual-basic/language-reference/statements/set-statement) 删除 `Private` 关键字。  
  
## 请参阅  
 [Property 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)