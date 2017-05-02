---
title: "slice 方法 (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice 方法 (ArrayBuffer)
返回 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 的一部分。  
  
## 语法  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## 参数  
 `arrayBufferObj`  
 必需。  该部分将从中复制的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 对象。  
  
 `start`  
 必需。  要复制的开头部分的字节索引。  
  
 `end`  
 可选。  要复制的结尾部分的字节索引。  
  
## 备注  
 `slice` 方法将返回包含 `arrayBufferObj` 指定部分的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 对象。  
  
 `slice` 方法可以复制最多（但不包括） `end` 指示的字节。  如果 `start` 或 `end` 为负，指定的索引将分别被视为 `length` \+ `start` 或 `end`，其中 `length` 是 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) 的长度。  如果省略了 `end`，将继续提取，直到 `arrayBufferObj` 的结尾。  如果 `end` 出现在 `start` 之前，则不会将任何字节复制到新的 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## 示例  
 下面的示例演示如何使用 `slice` 方法。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## 要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 请参阅  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)