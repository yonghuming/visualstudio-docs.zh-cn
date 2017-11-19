---
title: "Int8Array 对象 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3f85a505f41f2909330e938f4978433fc823f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="int8array-object"></a>Int8Array 对象
8 位整数值的类型化数组。 内容将初始化为 0。 如果无法分配请求数目的字节，则将引发异常。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>参数  
 `int8Array`  
 必需。 `Int8Array` 对象分配到的变量名称。  
  
 `length`  
 指定数组中元素的数目。  
  
 `array`  
 包含在此数组中的数组（或类型化数组）。 内容将初始化为给定数组或类型化数组的内容，且每个元素均转换为 Int8 类型。  
  
 `buffer`  
 Int8Array 表示的 ArrayBuffer。  
  
 `byteOffset`  
 可选。 指定与应开始 Int8Array 的缓冲区开始处的偏移量（以字节为单位）。  
  
 `length`  
 数组中的元素数。  
  
## <a name="constants"></a>常量  
 下表列出了 `Int8Array` 对象的常量。  
  
|常量|描述|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 常量](../../javascript/reference/bytes-per-element-constant-int8array.md)|数组中每个元素的大小（以字节为单位）。|  
  
## <a name="properties"></a>属性  
 下表列出了 `Int8Array` 对象的常量。  
  
|属性|描述|  
|--------------|-----------------|  
|[buffer 属性](../../javascript/reference/buffer-property-int8array.md)|只读。 获取此数组引用的 ArrayBuffer。|  
|[byteLength 属性](../../javascript/reference/bytelength-property-int8array.md)|只读。 此数组距离其 ArrayBuffer 开始处的长度（以字节为单位），在构造时已固定。|  
|[byteOffset 属性](../../javascript/reference/byteoffset-property-int8array.md)|只读。 此数组与其 ArrayBuffer 开始处的偏移量（以字节为单位），在构造时已固定。|  
|[length 属性](../../javascript/reference/length-property-int8array.md)|数组的长度。|  
  
## <a name="methods"></a>方法  
 下表列出了 `Int8Array` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[set 方法 (Int8Array)](../../javascript/reference/set-method-int8array.md)|设置值或值数组。|  
|[subarray 方法 (Int8Array)](../../javascript/reference/subarray-method-int8array.md)|为此数组获取 ArrayBuffer 存储的新的 Int8Array 视图。|  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 Int8Array 对象处理从 XmlHttpRequest 获取的二进制数据：  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]