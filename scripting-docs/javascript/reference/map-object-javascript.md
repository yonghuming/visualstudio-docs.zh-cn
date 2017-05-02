---
title: "Map 对象 (JavaScript) | Microsoft Docs"
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
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Map 对象 (JavaScript)
键\/值对的集合。  
  
## 语法  
  
```javascript  
mapObj = new Map()  
```  
  
## 备注  
 集合中的键和值可以是任何类型。  如果使用现有密钥向集合添加值，则新值会替换旧值。  
  
## 属性  
 下表列出了 `Map` 对象的属性。  
  
|Property|描述|  
|--------------|--------|  
|[构造函数](../../javascript/reference/constructor-property-map.md)|指定创建映射的函数。|  
|[Prototype — 原型](../../javascript/reference/prototype-property-map.md)|为映射返回对原型的引用。|  
|[size](../../javascript/reference/size-property-map-javascript.md)|返回映射中的元素数。|  
  
## 方法  
 下表列出了 `Map` 对象的方法。  
  
|方法|描述|  
|--------|--------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|从映射中移除所有元素。|  
|[删除](../../javascript/reference/delete-method-map-javascript.md)|从映射中移除指定的元素。|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|对映射中的每个元素执行指定操作。|  
|[get](../../javascript/reference/get-method-map-javascript.md)|返回映射中的指定元素。|  
|[有](../../javascript/reference/has-method-map-javascript.md)|如果映射包含指定元素，则返回 `true`。|  
|[set](../../javascript/reference/set-method-map-javascript.md)|添加一个新建元素到映射。|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|返回映射的字符串表示形式。|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|返回指定对象的原始值。|  
  
## 示例  
 下面的示例演示如何将成员添加到 `Map`，然后检索它们。  
  
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