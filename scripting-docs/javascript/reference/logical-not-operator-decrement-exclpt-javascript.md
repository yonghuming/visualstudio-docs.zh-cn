---
title: "逻辑“非”运算符 (!)(JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! 运算符"
  - "! 运算符, 关于 ! 运算符"
  - "逻辑非运算符"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 逻辑“非”运算符 (!)(JavaScript)
对一个表达式执行逻辑求反操作。  
  
## 语法  
  
```  
  
result = !expression  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression*  
 任何表达式。  
  
## 备注  
 下表阐释如何确定 *result*。  
  
|如果 `expression` 为|则 `result` 为|  
|-----------------------|------------------|  
|True|False|  
|False|True|  
  
 所有一元运算符（如 **\!** 运算符）都按照下面的规则来计算表达式：  
  
-   如果应用于未定义的表达式或 `null` 表达式，则会引发一个运行时错误。  
  
-   将对象转换为字符串。  
  
-   如果可能，将字符串转换为数字。  否则，将引发运行时错误。  
  
-   布尔值被视为数字（如果为 false，则为 0；如果为 true，则为 1）。  
  
 运算符将应用于结果数字。  
  
 对于 **\!** 运算符，如果 *expression* 不为零，则 *result* 为零。  如果 *expression* 为零，则 *result* 为 1。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位“取非”运算符 \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)