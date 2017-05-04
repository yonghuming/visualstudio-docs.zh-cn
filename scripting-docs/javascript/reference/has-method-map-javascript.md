---
title: "has 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (Map) (JavaScript)
如果映射包含指定元素，则返回 `true`。  
  
## 语法  
  
```javascript  
mapObj.has(key)  
```  
  
#### 参数  
 `mapObj`  
 必需。  `Map` 对象。  
  
 `key`  
 必需。  要测试的元素的键。  
  
## 属性值\/返回值  
 `true` 如果映射包含指定的元素。  
  
## 示例  
 下面的示例演示如何将成员添加到 `Map` 然后检查映射是否包含它。  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]