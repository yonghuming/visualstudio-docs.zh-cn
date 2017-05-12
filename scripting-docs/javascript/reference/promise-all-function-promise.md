---
title: "Promise.all 函数（承诺） | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.all 函数（承诺）
联接两个或更多承诺，并且仅在所有指定承诺均完成或被拒绝时返回。  
  
## 语法  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### 参数  
 `func1`  
 必需。  返回承诺的函数。  
  
 `func2`  
 必需。  返回承诺的函数。  
  
 `funcN`  
 可选。  返回承诺的一个或多个函数。  
  
## 备注  
 返回的结果是由已完成承诺返回的值构成的数组。  如果一个联接的承诺被拒绝，则 `Promise.all` 立即返回拒绝承诺的原因（所有其他返回值将被丢弃）。  
  
## 示例  
 在此代码中，对超时的首次调用在 5000 ms 后返回。  完成处理程序调用 `Promise.all`，它仅在对超时的两次调用均完成或被拒绝时返回。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)