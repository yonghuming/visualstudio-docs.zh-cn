---
title: "delete 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete 方法 (Set) (JavaScript)
从集中移除指定的元素。  
  
## 语法  
  
```javascript  
setObj.delete(value)  
```  
  
#### 参数  
 `setObj`  
 必需。  `Set` 对象。  
  
 `value`  
 必需。  要移除的元素。  
  
## 属性值\/返回值  
 `true` 如果该元素已被移除。  
  
## 示例  
 下面的示例演示如何将成员添加到 `Set`，然后删除其中之一。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]