---
title: "toString 方法 (Boolean) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString 方法 (Boolean)
返回对象的字符串表示形式。  
  
## 语法  
  
```  
  
boolean.toString()  
```  
  
## 参数  
 `boolean`  
 必需。  要获取其字符串表示形式的对象。  
  
## 返回值  
 如果布尔值为 `true`，则返回“true”。  否则返回“false”。  
  
## 备注  
  
## 示例  
 下面的示例阐释了 **toString** 方法的用法。  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]