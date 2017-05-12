---
title: "forEach 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# forEach 方法 (Map) (JavaScript)
对映射中的每个元素执行指定操作。  
  
## 语法  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### 参数  
 `mapObj`  
 必需。  `Map` 对象。  
  
 `callbackfn`  
 必需。  对于映射中的每个元素，`forEach` 都会调用函数一次。  `callbackfn` 最多接受三个参数。  对于映射中的每个元素，`forEach` 都会调用 `callbackfn` 函数一次。  
  
 `thisArg`  
 可选。  可在 `callbackfn` 函数中为其引用 `this` 关键字的对象。  如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。  
  
## 异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## 备注  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, key, mapObj)`  
  
 您可以使用最多三个参数声明回调函数，如下表所示。  
  
|回调参数|定义|  
|----------|--------|  
|`value`|映射中包含的值。|  
|`key`|包含在映射中的密钥。|  
|`mapObj`|要遍历的 `Map` 对象。|  
  
## 示例  
 下面的示例演示了如何通过使用 `forEach` 检索 `Map` 的成员。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]