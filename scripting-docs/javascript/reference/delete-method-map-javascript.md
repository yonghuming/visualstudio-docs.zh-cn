---
title: "delete 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete 方法 (Map) (JavaScript)
从映射中移除指定的元素。  
  
## 语法  
  
```javascript  
mapObj.delete(key)  
```  
  
#### 参数  
 `mapObj`  
 必需。  `Map` 对象。  
  
 `key`  
 必需。  要移除的元素的键。  
  
## 属性值\/返回值  
 `true` 如果该元素已被移除。  
  
## 示例  
 下面的示例演示如何将成员添加到 `Map`，然后删除其中之一。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]