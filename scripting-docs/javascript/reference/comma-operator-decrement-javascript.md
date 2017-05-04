---
title: "逗号运算符 (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "逗号运算符"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 逗号运算符 (,) (JavaScript)
顺序执行两个表达式。  
  
## 语法  
  
```  
  
expression1, expression2  
```  
  
## 参数  
 `expression1`  
 任何表达式。  
  
 `expression2`  
 任何表达式。  
  
## 备注  
 `,` 运算符会导致按从左到右的顺序执行表达式。  `,` 运算符的常见用法是在 `for` 循环的增量表达式中使用。  例如：  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for` 语句只允许在每次通过循环的结尾时执行单个表达式。  `,` 运算符允许将多个表达式视为单个表达式，因此这两个变量都可以递增。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)