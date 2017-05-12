---
title: "应为函数 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 应为函数
尝试了对非 `Function` 对象的对象调用某个**函数原型**方法，或在函数调用上下文中使用了对象。  例如，以下代码产生此错误，因为 **example** 不是函数。  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### 更正此错误  
  
-   仅对 `Function` 对象调用**函数原型**方法。  
  
-   确保将函数调用运算符 `()` 仅用于调用函数。  
  
## 请参阅  
 [Function 对象](../../javascript/reference/function-object-javascript.md)   
 [prototype 属性（对象）](../../javascript/reference/prototype-property-object-javascript.md)