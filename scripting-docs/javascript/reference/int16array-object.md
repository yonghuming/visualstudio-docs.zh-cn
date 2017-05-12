---
title: "Int16Array 对象 | Microsoft Docs"
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int16Array 对象
16 位整数值的类型化数组。  内容将初始化为 0。  如果无法分配请求数目的字节，则将引发异常。  
  
## 语法  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## 参数  
 `int16Array`  
 必选。  **Int16Array** 对象分配到的变量名称。  
  
 `length`  
 指定数组中元素的数目。  
  
 `array`  
 该数组中包含的数组（或类型化数组）。  内容将初始化为给定数组或类型化数组的内容，且每个元素均转换为 Int16 类型。  
  
 `buffer`  
 Int16Array 表示的 ArrayBuffer。  
  
 `byteOffset`  
 可选。  指定与 Int16Array 将开始的缓冲区开始处的偏移量（以字节为单位）。  
  
 `length`  
 数组中的元素数。  
  
## 常量  
 下表列出了 `Int16Array` 对象的常量。  
  
|常量|说明|  
|--------|--------|  
|[BYTES\_PER\_ELEMENT 常量](../../javascript/reference/bytes-per-element-constant-int16array.md)|数组中每个元素的大小（以字节为单位）。|  
  
## 属性  
 下表列出了 `Int16Array` 对象的常量。  
  
|属性|说明|  
|--------|--------|  
|[buffer 属性](../../javascript/reference/buffer-property-int16array.md)|只读。  获取此数组引用的 ArrayBuffer。|  
|[byteLength 属性](../../javascript/reference/byteoffset-property-int16array.md)|只读。  此数组距离其 ArrayBuffer 开始处的长度（以字节为单位），在构造时已固定。|  
|[byteOffset 属性](../../javascript/reference/byteoffset-property-int16array.md)|只读。  此数组与其 ArrayBuffer 开始处的偏移量（以字节为单位），在构造时已固定。|  
|[length 属性](../../javascript/reference/length-property-int16array.md)|数组的长度。|  
  
## 方法  
 下表列出了 `Int16Array` 对象的方法。  
  
|方法|说明|  
|--------|--------|  
|[set 方法 \(Int16Array\)](../../javascript/reference/set-method-int16array.md)|设置值或值数组。|  
|[subarray 方法 \(Int16Array\)](../../javascript/reference/subarray-method-int16array.md)|为此数组获取 ArrayBuffer 存储的新 Int16Array 视图。|  
  
## 示例  
 以下示例演示如何使用 Int16Array 对象处理从 XmlHttpRequest 获取的二进制数据：  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]