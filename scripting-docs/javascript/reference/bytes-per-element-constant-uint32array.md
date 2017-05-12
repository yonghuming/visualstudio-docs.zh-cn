---
title: "BYTES_PER_ELEMENT 常量 (Uint32Array) | Microsoft Docs"
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
ms.assetid: 9a82d1bf-0e97-4e14-b86f-343ccc8dfac2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BYTES_PER_ELEMENT 常量 (Uint32Array)
数组中每个元素的大小（以字节为单位）。  
  
## 语法  
  
```javascript  
var arraySize = uint32Array.BYTES_PER_ELEMENT;  
```  
  
## 示例  
 下面的示例演示如何获取数组元素的大小。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]