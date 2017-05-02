---
title: "Promise 对象 (JavaScript) | Microsoft Docs"
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
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Promise 对象 (JavaScript)
提供用于安排使用尚未计算的值进行工作的机制。  这是用于管理与异步 API 的交互的抽象对象。  
  
## 语法  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### 参数  
 `promise`  
 必需。  承诺分配到的变量名称。  
  
 `resolve`  
 必需。  一个函数，运行该函数可指示承诺已成功完成。  
  
 `reject`  
 可选。  一个函数，运行该函数可指示出现错误，承诺已被拒绝。  
  
## 备注  
 承诺必须完成（返回一个值）或者必须被拒绝（返回一个原因）。  承诺完成或被拒绝时（无论哪一个先发生），Promise 对象的 `then` 方法都会运行。  如果承诺成功完成，则将运行 `then` 方法的履行处理程序函数。  如果承诺被拒绝，则将运行 `then` 方法（或 `catch` 方法）的错误处理程序函数。  
  
## 示例  
 下面的示例演示如何调用返回承诺的函数 \(`timeout`\)。  达到 5000 ms 的超时时间后，将运行 `then` 方法的履行处理程序。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## 示例  
 还可以将调用链接到 `then` 方法，如下面的代码所示。  每个完成处理程序本身必须返回一个承诺来支持链接。  在此代码中，调用了相同 `timeout` 函数，对超时的首次调用在 1000 ms 后返回。  第一个完成处理程序再次调用 `timeout`，并在 2000 ms 后返回此承诺。  然后，其完成处理程序引发错误。  错误处理程序调用 `Promise.all`，它仅在对超时的两次调用均完成或被拒绝时返回。  
  
```javascript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 函数  
 下表介绍了 `Promise` 对象的函数。  
  
|函数|说明|  
|--------|--------|  
|[Promise.all 函数](../../javascript/reference/promise-all-function-promise.md)|联接两个或更多承诺，并且仅在所有指定承诺均完成或被拒绝时返回。|  
|[Promise.race 函数](../../javascript/reference/promise-race-function-promise.md)|创建一个新承诺，使其在传入参数中以第一个承诺解决或拒绝时所用的相同结果值进行解决或拒绝。|  
|[Promise.reject 函数](../../javascript/reference/promise-reject-function-promise.md)|创建新的已拒绝承诺，其结果等于传入的参数。|  
|[Promise.resolve 函数](../../javascript/reference/promise-resolve-function-promise.md)|创建新的已解决承诺，该承诺的结果等于其参数。|  
  
## 方法  
 下表介绍了 `Promise` 对象的方法。  
  
|方法|说明|  
|--------|--------|  
|[catch 方法](../../javascript/reference/catch-method-promise.md)|允许你指定承诺遭到拒绝时要执行的工作。|  
|[then 方法](../../javascript/reference/then-method-promise.md)|允许你指定实现承诺时要完成的工作。|