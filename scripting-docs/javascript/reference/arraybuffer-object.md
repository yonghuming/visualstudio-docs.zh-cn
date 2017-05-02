---
title: "ArrayBuffer 对象 | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer 对象
表示二进制数据的原始缓冲区，可用于存储不同类型化数组的数据。  无法直接读取或写入 `ArrayBuffers`，但是可以根据需要将其传递到类型化数组或 [DataView 对象](../../javascript/reference/dataview-object.md) 来解释原始缓冲区。  
  
 有关类型化数组的更多信息，请参见 [类型化数组](../../javascript/advanced/typed-arrays-javascript.md)。  
  
## 语法  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## 参数  
 `arrayBuffer`  
 必需。  `ArrayBuffer` 对象分配到的变量名称。  
  
 `length`  
 缓冲区的长度。  ArrayBuffer 的内容将初始化为 0。  如果无法分配请求数目的字节，则将引发异常。  
  
## 属性  
 下表列出了 `ArrayBuffer` 对象的属性。  
  
|属性|描述|  
|--------|--------|  
|[byteLength 属性](../../javascript/reference/bytelength-property-arraybuffer.md)|只读。  ArrayBuffer 的长度（以字节为单位）。|  
  
## 函数  
 下表列出了 `ArrayBuffer` 对象的函数。  
  
|属性|描述|  
|--------|--------|  
|[ArrayBuffer.isView 函数](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|确定对象是否提供缓冲区的视图。|  
  
## 方法  
 下表列出了 `ArrayBuffer` 对象的方法。  
  
|属性|描述|  
|--------|--------|  
|[slice 方法](../../javascript/reference/slice-method-arraybuffer.md)|返回 `ArrayBuffer` 的一部分。|  
  
## 示例  
 以下示例演示如何使用 ArrayBuffer 对象处理从 [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) 获取的二进制数据。  可以使用 [DataView 对象](../../javascript/reference/dataview-object.md) 来获取单个值。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 备注  
 有关使用 `XmlHttpRequest` 的详细信息，请参见[XMLHttpRequest enhancements](http://msdn.microsoft.com/zh-cn/be09137c-6546-441b-b953-dcbf72b77069)。  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]