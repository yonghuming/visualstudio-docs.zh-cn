---
title: "get 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get 方法 (Map) (JavaScript)
返回映射中的指定元素。  
  
## 语法  
  
```javascript  
mapObj.get(key)  
```  
  
#### 参数  
 `mapObj`  
 必需。  `Map` 对象。  
  
 `key`  
 必需。  `Map` 中元素的键。  
  
## 属性值\/返回值  
 返回与此键关联的对象。  如果 `Map` 不包含该键，则此方法返回一个 `undefined` 值。  
  
## 示例  
 下面的示例演示了如何从 `Map` 对象中检索元素。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]