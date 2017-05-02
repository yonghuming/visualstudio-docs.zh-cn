---
title: "setUint8 方法 (DataView) | Microsoft Docs"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint8 方法 (DataView)
在相对于视图开始处的指定字节偏移量位置处存储 Uint8 值。  
  
## 语法  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## 参数  
 `byteOffset`  
 缓冲区中将设置该值的位置。  
  
 `value`  
 要设置的值。  
  
## 备注  
 如果这些方法在视图末尾之外进行写入，则将引发异常。  
  
## 示例  
 下面的示例演示如何在 DataView 中设置第一个 Uint8。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]