---
title: "WeakMap 对象 (JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap 对象 (JavaScript)
键\/值对集合，其中每个键都是一个对象引用。  
  
## 语法  
  
```  
weakmapObj = new WeakMap()  
```  
  
## 备注  
 `WeakMap` 对象不能枚举。  
  
 如果使用现有密钥向集合添加值，则新值会替换旧值。  
  
 在 `WeakMap` 对象中，对键对象的引用保持“较弱”。  这意味着 `WeakMap` 不会阻止在密钥对象上进行垃圾回收。  当没有指向键对象的引用（除了 `WeakMap`）时，垃圾回收器可以回收键对象。  
  
## 属性  
 下表列出了 `WeakMap` 对象的属性。  
  
|Property|描述|  
|--------------|--------|  
|[构造函数](../../javascript/reference/constructor-property-weakmap.md)|指定创建 `WeakMap` 的函数。|  
|[Prototype — 原型](../../javascript/reference/prototype-property-weakmap.md)|为 `WeakMap` 返回对原型的引用。|  
  
## 方法  
 下表列出了 `WeakMap` 对象的方法。  
  
|方法|描述|  
|--------|--------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|从 `WeakMap` 中移除所有元素。|  
|[删除](../../javascript/reference/delete-method-weakmap-javascript.md)|从 `WeakMap` 中移除指定的元素。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|从 `WeakMap` 中返回指定的元素。|  
|[有](../../javascript/reference/has-method-weakmap-javascript.md)|如果 `WeakMap` 包含指定元素，则返回 `true`。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|添加新元素至 `WeakMap`。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|返回 `WeakMap` 的字符串表示形式。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|返回指定对象的原始值。|  
  
## 示例  
 下面的示例演示如何将成员添加到 `WeakMap`对象，然后检索它们。  
  
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