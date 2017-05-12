---
title: "add 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# add 方法 (WeakSet) (JavaScript)
将新元素添加到 `WeakSet`。  
  
## 语法  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### 参数  
 `weaksetObj`  
 必需。  一个 `WeakSet` 对象。  
  
 `obj`  
 必需。  `WeakSet` 的新元素。  
  
## 备注  
 新元素必须是一个对象，而不是任意值，并且必须是唯一的。  如果将非唯一的元素添加到 `WeakSet`，则新元素不会添加到集合中。  
  
## 示例  
 以下示例演示如何将成员添加到集并验证它们已被添加。  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]