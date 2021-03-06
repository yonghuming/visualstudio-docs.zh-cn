---
title: "Option Strict On 不允许将类型 Object 的操作数用于运算符“&lt;operatorname&gt;” | Microsoft Docs"
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
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On 不允许将类型 Object 的操作数用于运算符“&lt;operatorname&gt;”
Option Strict On 不允许将类型 Object 的操作数用于运算符“\<operatorname\>”。 请使用 Is 运算符测试对象标识。  
  
 当 `Option Strict` 为 `On` 时，将算数比较运算符（如 `=`）与一个或多个对象变量一起使用。  
  
 **错误 ID：**BC32013  
  
### 更正此错误  
  
1.  如果对象变量包含数值，并且需要进行算数比较，则转换为 `Option Strict Off`。  
  
2.  使用 `Is` 运算符比较对象标识。  
  
## 请参阅  
 [比较运算符](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Is 运算符](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Option Strict 语句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)