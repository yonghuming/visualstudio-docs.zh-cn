---
title: "set 方法 (Uint8Array) | Microsoft Docs"
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
ms.assetid: 6b0b48d5-e419-4c3c-98ed-d94cbe56e95d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# set 方法 (Uint8Array)
设置值或值数组。  
  
## 语法  
  
```javascript  
uint8Array.set(index, value);  
uint8Array.set(array, offset);  
  
```  
  
## 参数  
 `index`  
 要设置的位置的索引。  
  
 `value`  
 要设置的值。  
  
 `array`  
 要设置的值的类型化或非类型化数组。  
  
 `offset`  
 要写入的值在当前数组中的位置的索引。  
  
## 备注  
 如果输入数组为 TypedArray，则两个数组可以使用相同的基础 ArrayBuffer。  在此情况下，设置值时，就好像先将所有数据复制到未与任一数组重叠的临时缓冲区，然后再将临时缓冲区中的数据复制到当前数组中一样。  
  
 如果偏移量加上给定数组的长度超出当前 TypedArray 的范围，则将引发异常。  
  
## 示例  
 下面的示例演示如何设置数组的第一个元素。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8Array(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]