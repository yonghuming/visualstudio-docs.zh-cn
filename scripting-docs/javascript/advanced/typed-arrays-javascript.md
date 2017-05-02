---
title: "类型化数组 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 类型化数组 (JavaScript)
可以使用类型化数组来处理来自网络协议、二进制文件格式和原始图形缓冲区等源的二进制数据。  类型化数组还可用于管理具有已知字节布局的内存中二进制数据。  
  
## 示例  
 以下代码显示如何将 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)用作 [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) 的响应。  可以通过使用 [DataView 对象](../../javascript/reference/dataview-object.md)的不同方法，或通过将字节复制到适当的类型化数组，来操作响应中的字节。  
  
> [!TIP]
>  有关使用具有 `XmlHttpRequest` 的不同响应类型的详细信息，请参阅 [XMLHttpRequest.responseType](http://msdn.microsoft.com/zh-cn/8d7738d1-4bfd-4cf1-8015-174def089556)、[XMLHttpRequest 增强功能](http://msdn.microsoft.com/zh-cn/be09137c-6546-441b-b953-dcbf72b77069)和[下载不同类型的内容（Windows 应用商店应用）](http://msdn.microsoft.com/zh-cn/c0006bbd-17f9-4c6a-af81-2acaf109111d)。  
  
```javascript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## ArrayBuffer  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)表示用于存储不同类型化数组的数据的原始数据缓冲区。  无法读取或写入 `ArrayBuffer`，但可以将它传递给类型化数组或 [DataView 对象](../../javascript/reference/dataview-object.md) 来解释原始缓冲区。  可以使用 `ArrayBuffer` 来存储任何类型的数据（或混合类型的数据）。  
  
## DataView  
 可以使用 [DataView 对象](../../javascript/reference/dataview-object.md)来读取不同类型的二进制数据，并将它写入 `ArrayBuffer` 中的任何位置。  
  
## 类型化数组  
 类型化数组的类型表示可对其创建索引和进行操作的 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)的视图。  所有数组类型都具有固定长度。  
  
||||  
|-|-|-|  
|名称|大小（以字节为单位）|描述|  
|[Int8Array 对象](../../javascript/reference/int8array-object.md)|1|8 位补码带符号整数|  
|[Uint8Array 对象](../../javascript/reference/uint8array-object.md)|1|8 位无符号整数|  
|[Int16Array 对象](../../javascript/reference/int16array-object.md)|2|16 位补码带符号整数|  
|[Uint16Array 对象](../../javascript/reference/uint16array-object.md)|2|16 位无符号整数|  
|[Int32Array 对象](../../javascript/reference/int32array-object.md)|4|32 位补码带符号整数|  
|[Uint32Array 对象](../../javascript/reference/uint32array-object.md)|4|32 位无符号整数|  
|[Float32Array 对象](../../javascript/reference/float32array-object.md)|4|32 位 IEEE 浮点|  
|[Float64Array 对象](../../javascript/reference/float64array-object.md)|8|64 位 IEEE 浮点|