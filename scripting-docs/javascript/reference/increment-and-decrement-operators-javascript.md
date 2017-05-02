---
title: "递增 (++) 和递减 (--) 运算符 (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "递增运算符，语法"
  - "++ 运算符"
  - "++ 运算符，关于 ++ 运算符"
  - "递增运算符，语法"
  - "-- 运算符"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 递增 (++) 和递减 (--) 运算符 (JavaScript)
增量运算符将某个变量的值加一；减量运算符将某个变量的值减一。  
  
## 语法  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## 参数  
 `result`  
 任何变量。  
  
 `variable`  
 任何变量。  
  
## 备注  
 如果运算符在变量的前面出现，则在计算表达式之前修改该值。  如果运算符在变量的后面出现，则在计算表达式之后修改该值。  换句话说，给定 `j = ++k;` 的情况下，`j` 的值为 `k` 的原始值加一；给定 `j = k++;` 的情况下，`j` 的值为 `k` 的原始值，后者在其值赋给 `j` 后递增。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)