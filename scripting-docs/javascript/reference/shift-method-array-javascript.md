---
title: "shift 方法 (Array) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift 方法"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift 方法 (Array) (JavaScript)
从数组中移除第一个元素并将返回该元素。  
  
## 语法  
  
```  
  
arrayObj.shift( )  
```  
  
#### 参数  
 必需的 `arrayObj` 引用是 `Array` 对象。  
  
## 返回值  
 返回从数组中移除的元素。  
  
## 备注  
 下面的示例演示 `shift` 方法的用法。  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [unshift 方法 \(Array\)](../../javascript/reference/unshift-method-array-javascript.md)