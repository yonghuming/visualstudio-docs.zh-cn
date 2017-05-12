---
title: "减法运算符 (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- 运算符"
  - "- 运算符, 关于 - 运算符"
  - "算术运算符, 减法"
  - "非运算符"
  - "运算符, 减法"
  - "减法运算符, 语法"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 减法运算符 (-) (JavaScript)
从一个表达式的值中减去另一个表达式的值，若只有一个表达式时则取其相反数。  
  
## 语法  
  
```  
  
result = number1 - number2;  
  
```  
  
## 参数  
 *result*  
 任何数值变量。  
  
 `number`  
 任何数值表达式。  
  
 `number1`  
 任何数值表达式。  
  
 `number2`  
 任何数值表达式。  
  
## 备注  
 在语法 1 中，**\-** 运算符是用于计算两个数差值的算术减法运算符。  在语法 2 中，**\-** 运算符用作一元求反运算符，指示表达式的负值。  
  
 对于语法 2，和所有一元运算符一样，按如下规则计算表达式：  
  
-   如果应用于未定义的表达式或 `null` 表达式，则会引发一个运行时错误。  
  
-   将对象转换为字符串。  
  
-   如果可能，将字符串转换为数字。  否则，将引发运行时错误。  
  
-   布尔值被视为数字（如果为 false，则为 0；如果为 true，则为 1）。  
  
 运算符将应用于结果数字。  在语法 2 中，如果结果数字不是零，则 *result* 与结果数字符号颠倒后的值相等。  如果结果数字为零，则 *result* 为零。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [减法赋值运算符 \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)