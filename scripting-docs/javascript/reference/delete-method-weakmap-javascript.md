---
title: "delete 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete 方法 (WeakMap) (JavaScript)
从 `WeakMap` 对象中移除指定的元素。  
  
## 语法  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### 参数  
 `weakmapObj`  
 必需。  `WeakMap` 对象。  
  
 `key`  
 必需。  要移除的元素的键。  
  
## 属性值\/返回值  
 `true` 如果该元素已被移除。  
  
## 示例  
 下面的示例演示如何将成员添加到 `WeakMap`，然后将其删除。  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]