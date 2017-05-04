---
title: "has 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# has 方法 (WeakSet) (JavaScript)
如果 `WeakSet` 包含指定的元素，则返回 `true`。  
  
## 语法  
  
```javascript  
setObj.has(obj)  
```  
  
#### 参数  
 `setObj`  
 必需。  一个 `WeakSet` 对象。  
  
 `obj`  
 必需。  要测试的元素。  
  
## 属性值\/返回值  
 如果该集包含指定的元素，则为 `true`。  
  
## 示例  
 下面的示例演示如何将成员添加到 `WeakSet`，然后检查集是否包含特定成员。  
  
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