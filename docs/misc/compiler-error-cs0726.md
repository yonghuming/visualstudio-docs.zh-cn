---
title: "编译器错误 CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0726
“format specifier”不是有效的格式说明符  
  
 此错误将出现在调试器中。 在某一调试器窗口中键入变量名时，可在其后加一个逗号，再加一个格式说明符。 示例包括：`myInt, h` 或 `myString,nq`。 当编译器无法识别 [C\# 中的格式说明符](../debugger/format-specifiers-in-csharp.md) 时，此错误出现。