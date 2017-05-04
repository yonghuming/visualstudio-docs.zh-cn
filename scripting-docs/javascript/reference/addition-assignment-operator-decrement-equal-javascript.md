---
title: "加法赋值运算符 (+=) (JavaScript) | Microsoft Docs"
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
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "加法赋值运算符 (+=)"
  - "+= 运算符"
  - "赋值运算符，JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 加法赋值运算符 (+=) (JavaScript)
将变量值与表达式值相加，并将结果赋给该变量。  
  
## 语法  
  
```  
  
result += expression   
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `expression`  
 任何表达式。  
  
## 备注  
 使用此运算符与指定 `result = result + expression` 完全相同。  
  
 这两个表达式的类型决定 `+=` 运算符的行为。  
  
|如果|则|  
|--------|-------|  
|两个表达式都为数字或布尔型|添加|  
|两个表达式都是字符串|连接|  
|一个表达式为数字，而另一个表达式为字符串|连接|  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [加法运算符 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)