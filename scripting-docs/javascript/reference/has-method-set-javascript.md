---
title: "has 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (Set) (JavaScript)
如果集包含指定元素，则返回 `true`。  
  
## 语法  
  
```javascript  
setObj.has(value)  
```  
  
#### 参数  
 `setObj`  
 必需。  `Set` 对象。  
  
 `value`  
 必需。  要测试的元素。  
  
## 属性值\/返回值  
 `true` 如果集包含指定的元素。  
  
## 示例  
 下面的示例演示如何将成员添加到 `Set`，然后检查该设置是否包含特定的成员。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]