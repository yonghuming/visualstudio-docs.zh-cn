---
title: "值参数中不支持循环引用 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 值参数中不支持循环引用
已尝试调用具有无效值的 `JSON.stringify`。  `value` 参数（一个数组或对象）包含循环引用。  
  
### 更正此错误  
  
-   从参数中删除循环引用。  
  
## 示例  
 在此示例中，代码导致运行时错误，因为 `john` 具有对 `mary` 的引用，而 `mary` 又引用了 `john`。  要移除该循环引用，请移除或取消 `mary` 对象的 `brother` 属性，或 `john` 对象的 `sister` 属性。  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## 请参阅  
 [JSON 对象](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函数](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 运行时错误](../../javascript/reference/javascript-run-time-errors.md)