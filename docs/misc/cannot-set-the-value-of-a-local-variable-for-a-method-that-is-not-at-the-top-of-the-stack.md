---
title: "无法设置不是位于堆栈顶部的方法的局部变量值 | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法设置不是位于堆栈顶部的方法的局部变量值
如果变量位于调用堆栈的顶部，你才能对其修改。 例如，如果 `procedure1` 调用 `procedure2` 且你处于 `procedure1`，则不能修改 `procedure2` 中的变量。  
  
 **错误 ID：**BC30711  
  
### 更正此错误  
  
-   修改位于调用堆栈顶部的变量。  
  
## 请参阅  
 [使用 Visual Studio 进行调试](../debugger/debugging-in-visual-studio.md)