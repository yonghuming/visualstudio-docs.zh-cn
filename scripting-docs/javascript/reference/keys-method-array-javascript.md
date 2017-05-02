---
title: "keys 方法（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: fc5b6a30-642c-4bd7-ad31-a42667af2f3f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# keys 方法（数组）(JavaScript)
返回一个迭代器，它能返回数组的索引值。  
  
## 语法  
  
```  
arrayObj.keys();  
```  
  
#### 参数  
 `arrayObj`  
 必需。  数组对象。  
  
## 备注  
  
## 示例  
 下面的示例演示如何获取数组的键值。  
  
```javascript  
var k = ["a", "b", "c"].keys();  
// k.next().value == 0  
// k.next().value == 1  
// k.next().value == 2   
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]