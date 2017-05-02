---
title: "forEach 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach 方法 (Set) (JavaScript)
对集合中的每个元素执行指定操作。  
  
## 语法  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### 参数  
 `setObj`  
 必需。  `Set` 对象。  
  
 `callbackfn`  
 必需。  `callbackfn` 最多接受三个参数。  对于集合中的每个元素，`forEach` 都会调用函数一次。  
  
 `thisArg`  
 可选。  可在 `callbackfn` 函数中为其引用 `this` 关键字的对象。  如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。  
  
## 异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## 备注  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, key, setObj)`  
  
 您可以使用最多三个参数声明回调函数，如下表所示。  
  
|回调参数|定义|  
|----------|--------|  
|`value`|集中包含的值。|  
|`key`|集中包含的值。  一组没有键，因此此值与 `value` 相同。|  
|`setObj`|要遍历的 `Set` 对象。|  
  
## 示例  
 下面的示例显示如何使用 `forEach`。  `callbackfn` 参数包含回调函数的代码。  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## 示例  
 下面的示例表明你还可以通过仅将单个参数传递给回调函数来从集中检索成员。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]