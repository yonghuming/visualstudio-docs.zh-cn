---
title: "Promise.race 函数（承诺） | Microsoft Docs"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.race 函数（承诺）
创建一个新承诺，使其在传入参数中以第一个承诺解决或拒绝时所用的相同结果值进行解决或拒绝。  
  
## 语法  
  
```  
Promise.race(iterable)  
  
```  
  
#### 参数  
 `iterable`  
 必需。  一个或多个承诺。  
  
## 备注  
 如果 `iterable` 中的一个承诺处于已解决或已拒绝状态，则 `Promise.race` 返回一个按相同方式解决或拒绝的承诺，即结果值等于用于解决（或拒绝）此承诺的值的方式。  如果 `iterable` 中的多个承诺已解决或已拒绝，则 `Promise.race` 返回一个按迭代第一个承诺的相同方式解决的承诺。  如果 iterable 中的承诺均不解决或拒绝，则从 `Promise.race` 返回的承诺也不进行解决或拒绝。  
  
## 示例  
  
```javascript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)