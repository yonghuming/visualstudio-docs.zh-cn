---
title: "“WithEvents”变量必须有“As”子句 | Microsoft Docs"
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
  - "vbc30412"
  - "bc30412"
helpviewer_keywords: 
  - "BC30412"
ms.assetid: 8c941523-8e5d-4bf0-8a52-772ecd5d5592
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “WithEvents”变量必须有“As”子句
未向 `As` 子句提供关键字 `WithEvents`。 将变量声明为可引发事件的特定类。  
  
 **错误 ID：**BC30412  
  
### 更正此错误  
  
1.  添加指定可引发事件的类的 `As` 子句。  
  
## 请参阅  
 [不在生成中：WithEvents 和 Handles 子句](http://msdn.microsoft.com/zh-cn/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim 语句](/dotnet/visual-basic/language-reference/statements/dim-statement)