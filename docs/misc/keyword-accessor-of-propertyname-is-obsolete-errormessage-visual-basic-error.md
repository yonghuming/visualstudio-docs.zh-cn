---
title: "“&lt;propertyname&gt;”的“&lt;keyword&gt;”访问器已过时：“&lt;errormessage&gt;”（Visual Basic 错误） | Microsoft Docs"
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
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;propertyname&gt;”的“&lt;keyword&gt;”访问器已过时：“&lt;errormessage&gt;”（Visual Basic 错误）
语句尝试读取或写入属性（已为此属性使用 <xref:System.ObsoleteAttribute> 特性和将其视为错误的指令对相应过程进行了标记）。  
  
 你可以通过将 <xref:System.ObsoleteAttribute> 应用到编程元素，以将其标记为不再使用。 如果执行此操作，则可以将特性的 <xref:System.ObsoleteAttribute.IsError%2A> 属性设置为 `True` 或 `False`。 如果设置为 `True`，编译器将尝试将该元素用作错误。 如果设置为 `False`，或让它默认为 `False`，则编译器会在尝试使用该元素时发出警告。  
  
 **错误 ID：**BC30911  
  
### 更正此错误  
  
1.  检查引用的错误消息并采取相应的操作。  
  
2.  确保源代码引用拼写的属性名称正确无误。  
  
3.  避免以生成此消息的方式（读取或写入）访问属性。  
  
## 请参阅  
 [不在生成中：Visual Basic 中使用的属性](http://msdn.microsoft.com/zh-cn/22231318-8a40-49af-9245-e0aab723563b)   
 [不在生成中：属性的应用](http://msdn.microsoft.com/zh-cn/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Property 过程](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)