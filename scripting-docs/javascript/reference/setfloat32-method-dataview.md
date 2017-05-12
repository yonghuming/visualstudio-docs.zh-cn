---
title: "setFloat32 方法 (DataView) | Microsoft Docs"
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setFloat32 方法 (DataView)
在相对于视图开始处的指定字节偏移量位置处设置 Float32 值。  没有对齐约束；可按任何偏移量设置多字节值。  
  
## 语法  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
```  
  
## 参数  
 `byteOffset`  
 缓冲区中将用于检索该值的位置。  
  
 `value`  
 要设置的值。  
  
 `littleEndian`  
 可选。  如果为 false 或未定义，则应写入 big\-endian 值；否则应写入 little\-endian 值。  
  
## 备注  
 如果这些方法在视图末尾之外进行写入，则将引发异常。  
  
## 示例  
 下面的示例演示如何在 DataView 中设置第一个 Float32。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]