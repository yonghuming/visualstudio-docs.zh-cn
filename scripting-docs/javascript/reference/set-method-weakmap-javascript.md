---
title: "set 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set 方法 (WeakMap) (JavaScript)
向 `WeakMap` 对象添加新元素。  
  
## 语法  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### 参数  
 `weakmapObj`  
 必需。  一个 `WeakMap` 对象。  
  
 `key`  
 必需。  一个表示要添加元素的键的对象。  它必须是对象引用。  
  
 `value`  
 必需。  要添加的元素的值。  
  
## 属性值\/返回值  
 返回包含新键\/值对的 `WeakMap` 对象。  
  
## 备注  
 如果使用现有键向集合添加值，则新值会替换旧值。  
  
## 示例  
 以下示例演示如何向 `WeakMap` 对象添加成员。  
  
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
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]