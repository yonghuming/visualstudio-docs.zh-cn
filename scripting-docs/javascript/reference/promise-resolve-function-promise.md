---
title: "Promise.resolve 函数（承诺） | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.resolve 函数（承诺）
创建新的已解决承诺，该承诺的结果等于其参数。  
  
## 语法  
  
```  
Promise.resolve(x)  
```  
  
#### 参数  
 `x`  
 必需。  与已完成承诺一起返回的值。  
  
## 备注  
 当返回已完成承诺对象时，将运行 `then` 方法的履行处理函数。  
  
## 示例  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)