---
title: "get 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get 方法 (WeakMap) (JavaScript)
从 `WeakMap` 对象中返回指定的元素。  
  
## 语法  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### 参数  
 `weakmapObj`  
 必需。  `WeakMap` 对象。  
  
 `key`  
 必需。  `WeakMap` 中元素的键。  
  
## 属性值\/返回值  
 返回与此键关联的对象。  如果 `WeakMap` 不包含键，则此方法返回 `undefined` 值。  
  
## 示例  
 下面的示例演示了如何从 `WeakMap` 对象中检索成员。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]