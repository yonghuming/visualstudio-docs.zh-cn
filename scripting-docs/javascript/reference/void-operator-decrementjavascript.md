---
title: "void 运算符 (JavaScript) | Microsoft Docs"
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
  - "void_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "void 运算符"
ms.assetid: c054bc7e-8341-42e6-b227-4d7b196f60d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# void 运算符 (JavaScript)
禁止表达式返回值。  
  
## 语法  
  
```  
void expression   
```  
  
## 备注  
 `expression` 参数是任何有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 表达式。  
  
 `void` 运算符计算其表达式，并返回 `undefined`。  当应计算表达式，但又不希望脚本的其他部分看见其结果时，该运算符很有用。  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)