---
title: "delete 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# delete 方法 (WeakSet) (JavaScript)
从 `WeakSet` 中移除指定元素。  
  
## 语法  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### 参数  
 `weaksetObj`  
 必需。  一个 `WeakSet` 对象。  
  
 `obj`  
 必需。  要移除的元素。  
  
## 属性值\/返回值  
 如果已移除元素，则为 `true`。  
  
## 示例  
 下面的示例演示了如何添加和删除 `WeakSet` 的元素。  
  
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