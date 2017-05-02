---
title: "catch 方法（承诺） | Microsoft Docs"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# catch 方法（承诺）
允许你指定承诺遭到拒绝时要执行的工作。  
  
## 语法  
  
```  
  
promise.catch(onRejected)  
```  
  
#### 参数  
 `promise`  
 必需。  Promise 对象。  
  
 `onRejected`  
 必需。  在承诺遭到拒绝时要运行的错误处理程序函数。  
  
## 备注  
  
## 示例  
 在下面的代码示例中，对超时的首次调用在 5000 ms 后返回。  在此代码中，承诺遭到拒绝且运行错误处理程序函数。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]