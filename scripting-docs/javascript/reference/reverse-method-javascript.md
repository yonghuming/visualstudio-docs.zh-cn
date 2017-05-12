---
title: "reverse 方法 (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "数组 [Visual Studio]，转置元素"
  - "reverse 方法"
  - "转置元素"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse 方法 (JavaScript)
反转 `Array` 中的元素。  
  
## 语法  
  
```  
  
arrayObj.reverse()   
```  
  
## 参数  
 `arrayObj`  
 必需。  任意 `Array` 对象。  
  
## 返回值  
 反向数组。  
  
## 备注  
 必需的 `arrayObj` 引用是 `Array` 对象。  
  
 `reverse` 方法将一个 `Array` 对象中的元素按所在位置进行反转。  在执行过程中，此方法并不创建新 `Array` 对象。  
  
 如果数组是不连续的，则 `reverse` 方法将在数组中创建元素，这些元素将填充数组中的间隙。  所创建的这些元素的值具有值 `undefined`。  
  
## 示例  
 下面的示例演示 `reverse` 方法的用法。  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [concat 方法（数组）](../../javascript/reference/concat-method-array-javascript.md)