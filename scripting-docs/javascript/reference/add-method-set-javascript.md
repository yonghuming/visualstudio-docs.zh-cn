---
title: "add 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add 方法 (Set) (JavaScript)
向集添加新元素。  
  
## 语法  
  
```javascript  
setObj.add(value)  
```  
  
#### 参数  
 `setObj`  
 必需。  一个 `Set` 对象。  
  
 `value`  
 必需。  `Set` 的新元素。  
  
## 备注  
 新元素可以是任何类型，并且必须唯一。  如果将非唯一的元素添加到 `Set`，则新元素不会添加到集合中。  
  
## 示例  
 以下示例演示如何将成员添加到集，然后检索成员。  
  
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