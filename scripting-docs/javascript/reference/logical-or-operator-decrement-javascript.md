---
title: "逻辑或运算符 (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| 运算符"
  - "逻辑 OR 运算符"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 逻辑或运算符 (||) (JavaScript)
对两个表达式执行逻辑析取操作。  
  
## 语法  
  
```  
  
result = expression1 || expression2  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression1*  
 任何表达式。  
  
 *expression2*  
 任何表达式。  
  
## 备注  
 如果两个表达式中的一个或二者的计算结果为 **True**，则 *result* 为 **True**。  下表阐释如何确定 *result*：  
  
|如果 `expression1` 为|并且 `expression2` 为|则 `result` 为|  
|------------------------|------------------------|------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 使用下列规则将非布尔值转换为布尔值：  
  
-   所有对象都被视为 true。  
  
-   当且仅当字符串为空时才被视为 false。  
  
-   `null` 和未定义被认为是 false。  
  
-   当且仅当数字为 0 时才为 false。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)