---
title: "buffer 属性 (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# buffer 属性 (Uint8ClampedArray)
只读。  获取此数组引用的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## 语法  
  
```javascript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## 示例  
 下面的示例演示如何获取数组的 ArrayBuffer。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 请参阅  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)