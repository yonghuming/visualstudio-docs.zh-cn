---
title: "按位或赋值运算符 (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= 运算符"
  - "赋值运算符, 按位 [JavaScript]"
  - "按位运算符, OR 运算符"
  - "OR 运算符"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 按位或赋值运算符 (|=) (JavaScript)
对变量值与表达式值执行按位“或”运算，并将结果赋给该变量。  
  
## 语法  
  
```  
  
result |= expression  
```  
  
## 参数  
 *result*  
 任何变量。  
  
 *expression*  
 任何表达式。  
  
## 备注  
 使用此运算符与指定以下内容完全相同：  
  
```javascript  
result = result | expression  
```  
  
 **&#124;\=** 运算符查看 *result* 和 *expression* 的值的二进制表示形式，并对其执行按位“或”运算。  该运算的结果如下所示：  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 任何时候，只要两个表达式中的一个表达式的某位为 1，则结果中的该位为 1。  否则，结果中的该位为 0。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [按位“或”运算符 \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)