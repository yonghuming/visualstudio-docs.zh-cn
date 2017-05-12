---
title: "has 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (WeakMap) (JavaScript)
如果 `WeakMap` 对象包含指定的元素，则返回 `true`。  
  
## 语法  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### 参数  
 `weakmapObj`  
 必需。  `WeakMap` 对象。  
  
 `key`  
 必需。  要测试的元素的键。  
  
## 属性值\/返回值  
 `true` 如果 `WeakMap` 包含指定的键。  
  
## 示例  
 下面的示例演示如何将成员添加到 `WeakMap`，并用  `has` 检查它是否存在。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]