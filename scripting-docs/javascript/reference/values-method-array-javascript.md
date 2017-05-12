---
title: "values 方法（数组）(JavaScript) | Microsoft Docs"
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
ms.assetid: b20699d6-f8b1-4744-8551-9e81c82850dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# values 方法（数组）(JavaScript)
返回一个迭代器，它返回数组的值。  
  
## 语法  
  
```  
arrayObj.values();  
```  
  
#### 参数  
 `arrayObj`  
 必需。  数组对象。  
  
## 备注  
  
## 示例  
 下面的示例演示如何获取数组的值。  
  
```javascript  
var v = ["a", "b", "c"].values();  
// v.next().value == "a"  
// v.next().value == "b"  
// v.next().value == "c"   
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]