---
title: "get 方法 (Float64Array) | Microsoft Docs"
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
ms.assetid: debbe2f4-fe1e-4f9d-af7d-b24430bfa962
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# get 方法 (Float64Array)
可省略。  获取指定索引处的元素。  
  
## 语法  
  
```javascript  
var value = float64Array.get(index);  
```  
  
## 参数  
 `value`  
 此方法返回的值。  
  
 `index`  
 用于获取数组中的元素的索引。  
  
## 示例  
 下面的示例演示如何获取数组的第一个元素。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 4);  
            var element = floatArr.getFloat64(0);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]