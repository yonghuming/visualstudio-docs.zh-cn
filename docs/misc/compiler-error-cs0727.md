---
title: "编译器错误 CS0727 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0727
无效的格式说明符  
  
 此错误将出现在调试器中。 在某一调试器窗口中键入变量名时，可在其后加一个逗号，再加一个格式说明符。 示例有 myInt, h 或 myString, nq。 当编译器完全无法分析你键入的内容时，将出现此错误。 要解决此错误，请重新键入变量名称，可以选择后跟一个逗号和一个[有效的格式说明符](../debugger/format-specifiers-in-csharp.md)。