---
title: "“Inherits”只能在“Class”语句中出现一次，并且只能指定一个类 | Microsoft Docs"
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
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Inherits”只能在“Class”语句中出现一次，并且只能指定一个类
多个 `Inherits` 语句将出现在同一个类中，或 `Inherits` 语句会指定多个类。 类可以仅从一个基类继承。  
  
 **错误 ID：**BC30121  
  
### 更正此错误  
  
-   删除任何额外 `Inherits` 语句，并确保其余的 `Inherits` 语句仅指定一个基类。  
  
## 请参阅  
 [Inherits 语句](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [继承的基础知识](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)