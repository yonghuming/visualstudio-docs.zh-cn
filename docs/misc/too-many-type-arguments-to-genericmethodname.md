---
title: "“&lt;genericMethodName&gt;”的类型参数太多 | Microsoft Docs"
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
  - "bc32043"
  - "vbc32043"
helpviewer_keywords: 
  - "BC32043"
ms.assetid: c4d8f67a-4317-461a-9446-6717cfa1d888
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;genericMethodName&gt;”的类型参数太多
已使用多于类型形参的类型实参调用了泛型方法。  
  
 在调用泛型方法时，必须为此方法定义的每一个类型形参提供一个类型实参。  
  
 **错误 ID：**BC32043  
  
### 更正此错误  
  
-   从类型实参列表中删除类型实参，以便正在调用的泛型方法上的每一个类型形参都有一个类型实参。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [类型列表](/dotnet/visual-basic/language-reference/statements/type-list)