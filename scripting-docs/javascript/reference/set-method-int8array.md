---
title: "set 方法 (Int8Array) | Microsoft Docs"
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
ms.assetid: 4beae82e-8556-48aa-86c6-18c8859d913e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# set 方法 (Int8Array)
设置值或值的数组。  
  
## 语法  
  
```javascript  
int8Array.set(index, value);  
int8Array.set(array, offset);  
  
```  
  
## 参数  
 `index`  
 要设置的位置的索引。  
  
 `value`  
 要设置的值。  
  
 `array`  
 要设置的值的类型化或非类型化数组。  
  
 `offset`  
 当前数组中写入值的位置的索引。  
  
## 备注  
 如果输入数组为 TypedArray，则两个数组可以使用相同的基础 ArrayBuffer。  在此情况下，将设置值，就好像先将所有数据复制到未重叠任一数组的临时缓冲区，然后再将临时缓冲区中的数据复制到当前数组一样。  
  
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
            var intArr = new Int8Array(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]