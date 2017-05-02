---
title: "Promise.reject 函数（承诺） | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.reject 函数（承诺）
创建新的已拒绝承诺，其结果等于传入的参数。  
  
## 语法  
  
```  
Promise.reject(r);  
```  
  
#### 参数  
 `r`  
 必需。  承诺遭到拒绝的原因。  
  
## 备注  
 当返回被拒绝的承诺时，运行 `then` 或 `catch` 方法的错误处理函数。  
  
## 示例  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)