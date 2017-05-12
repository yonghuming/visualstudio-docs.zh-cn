---
title: "valueOf 方法 (Array) | Microsoft Docs"
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
ms.assetid: b694fe65-1297-4580-8af2-406932c06454
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf 方法 (Array)
返回指定对象的基元值。  
  
## 语法  
  
```  
  
array.valueOf()  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 返回数组实例。  
  
## 备注  
 在下面的示例中，实例化的数组对象与此方法的返回值相同。  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.valueOf();  
  
if (arr === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]