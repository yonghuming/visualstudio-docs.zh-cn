---
title: "subarray 方法 (Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray 方法 (Int8Array)
为此数组获取 ArrayBuffer 存储的新的 Int8Array 视图，并引用开始处的元素（含）直至末尾处的元素（不含）。  
  
## 语法  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## 参数  
 `newInt8Array`  
 此方法返回的子数组。  
  
 `begin`  
 数组开始处的索引。  
  
 `end`  
 数组结尾处的索引。  这是不包括在内的。  
  
## 备注  
 如果 begin 或 end 为负，则引用数组结尾处（而非数组开始处）的索引。  如果未指定 end，则子数组包含 TypedArray 的从开头到结尾的所有元素。  begin 和 end 值指定的范围将限制到当前数组的有效索引范围。  如果新 TypedArray 的计算长度为负，则会将其限制为零。  返回的 TypedArray 将与对其调用此方法的数组的类型相同。  
  
## 示例  
 以下示例演示如何获取一个长度为两个元素的子数组（从数组的第一个元素开始）。  
  
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
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]