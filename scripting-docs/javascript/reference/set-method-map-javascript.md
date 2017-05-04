---
title: "set 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set 方法 (Map) (JavaScript)
向映射添加新元素。  
  
## 语法  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### 参数  
 `mapObj`  
 必需。  一个 `Map` 对象。  
  
 `key`  
 必需。  新元素的键。  
  
 `value`  
 必需。  要添加的元素的值。  
  
## 属性值\/返回值  
 返回包含新键\/值对的 `Map` 对象。  
  
## 备注  
 如果使用现有键向集合添加值，则新值会替换旧值。  
  
## 示例  
 以下示例演示如何将成员添加到 `Map`，然后检索成员。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]