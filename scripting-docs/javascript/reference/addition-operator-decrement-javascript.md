---
title: "加法运算符 (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "算术运算符，加号"
  - "字符串 [Visual Studio]，串联"
  - "串联运算符，与加号运算符"
  - "加法运算符"
  - "+ 运算符"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 加法运算符 (+) (JavaScript)
将一个数值表达式的值与另一个数值表达式的值相加，或连接两个字符串。  
  
## 语法  
  
```  
  
result = expression1 + expression2  
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## 备注  
 这两个表达式的类型决定 **\+** 运算符的行为。  
  
|如果|则|  
|--------|-------|  
|两个表达式都为数字或布尔型|添加|  
|两个表达式都是字符串|连接|  
|一个表达式为数字，而另一个表达式为字符串|连接|  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [加法赋值运算符 \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)