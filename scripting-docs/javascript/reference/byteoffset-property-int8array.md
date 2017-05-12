---
title: "byteOffset 属性 (Int8Array) | Microsoft Docs"
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
ms.assetid: b155bf97-d567-4921-8edd-dbca0d84b6cf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# byteOffset 属性 (Int8Array)
只读。  此数组的从其 ArrayBuffer 开始的偏移量（以字节为单位）在构造时已固定。  
  
## 语法  
  
```javascript  
var arrayOffset = int8Array.byteOffset;  
```  
  
## 示例  
 下面的示例演示如何获取数组的偏移量。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]