---
title: "DataView 对象 | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DataView 对象
可使用 DataView 对象在 ArrayBuffer 中的任何位置读取和写入不同类型的二进制数据。  
  
## 语法  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## 参数  
 `dataView`  
 必需。  **DataView** 对象分配到的变量名称。  
  
 `buffer`  
 DataView 表示的 ArrayBuffer。  
  
 `byteOffset`  
 可选。  指定与 DataView 将开始的缓冲区开始处的偏移量（以字节为单位）。  
  
 `byteLength`  
 可选。  指定 DataView 将表示的缓冲区部分的长度（以字节为单位）。  
  
## 备注  
 如果省略 byteOffset 和 byteLength，则 DataView 将跨整个 ArrayBuffer 范围。  如果省略 byteLength，则 DataView 会从给定 byteOffset 开始扩展直至达到 ArrayBuffer 的结尾。  如果给定 byteOffset 和 byteLength 引用 ArrayBuffer 的结尾外部的区域，则会引发异常。  
  
## 属性  
 下表列出了 `DataView` 对象的属性。  
  
|Property|描述|  
|--------------|--------|  
|[缓冲区属性](../../javascript/reference/buffer-property-dataview.md)|只读。  获取此视图引用的 ArrayBuffer。|  
|[字节长度属性](../../javascript/reference/bytelength-property-dataview.md)|只读。  此视图从其 ArrayBuffer 开始的长度（以字节为单位）在构造时已固定。|  
|[byteOffset 属性](../../javascript/reference/byteoffset-property-dataview.md)|只读。  此视图从其 ArrayBuffer 开始的偏移量（以字节为单位）在构造时已固定。|  
  
## 方法  
 下表列出了 `DataView` 对象的方法。  
  
|方法|描述|  
|--------|--------|  
|[getInt8 方法](../../javascript/reference/getint8-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Int8 值。|  
|[getUint8 方法 \(DataView\)](../../javascript/reference/getuint8-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Uint8 值。|  
|[getInt16 方法 \(DataView\)](../../javascript/reference/getint16-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Int16 值。|  
|[getUint16 方法 \(DataView\)](../../javascript/reference/getuint16-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Uint16 值。|  
|[getInt32 方法 \(DataView\)](../../javascript/reference/getint32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Int32 值。|  
|[getUint32 方法 \(DataView\)](../../javascript/reference/getuint32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Uint32 值。|  
|[getFloat32 方法 \(DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Float32 值。|  
|[getFloat64 方法 \(DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处获取 Float64 值。|  
|[setInt8 方法 \(DataView\)](../../javascript/reference/setint8-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Int8 值。|  
|[setUint8 方法 \(DataView\)](../../javascript/reference/setuint8-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Uint8 值。|  
|[setInt16 方法 \(DataView\)](../../javascript/reference/setint16-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Int16 值。|  
|[setUint16 方法 \(DataView\)](../../javascript/reference/setuint16-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Uint16 值。|  
|[setInt32 方法 \(DataView\)](../../javascript/reference/setint32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Int32 值。|  
|[setUint32 方法 \(DataView\)](../../javascript/reference/setuint32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Uint32 值。|  
|[setFloat32 方法 \(DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Float32 值。|  
|[setFloat64 方法 \(DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|在相对于视图开始处的指定字节偏移量位置处存储 Float64 值。|  
  
## 示例  
 下面的示例演示如何使用 DataView 对象处理从 XmlHttpRequest 获取的二进制数据：  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]