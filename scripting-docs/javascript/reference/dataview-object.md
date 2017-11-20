---
title: "DataView 对象 |Microsoft 文档"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="dataview-object"></a>DataView 对象
DataView 对象可用于读取和写入 ArrayBuffer 中的任何位置的不同类型的二进制数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>参数  
 `dataView`  
 必需。 到的变量名称**DataView**分配对象。  
  
 `buffer`  
 数据视图表示的 ArrayBuffer。  
  
 `byteOffset`  
 可选。 以字节为单位的数据视图应开始的缓冲区开始从指定的偏移量。  
  
 `byteLength`  
 可选。 指定的缓冲区的数据视图应表示部分的长度 （以字节为单位）。  
  
## <a name="remarks"></a>备注  
 如果省略 byteOffset 和 byteLength，DataView 跨越整个 ArrayBuffer 范围。 如果省略 byteLength，DataView ArrayBuffer 结束之前一直扩展从给定 byteOffset。 如果给定的 byteOffset 和 byteLength 引用的 ArrayBuffer 末尾之外的区域，将引发异常。  
  
## <a name="properties"></a>属性  
 下表列出了 `DataView` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[buffer 属性](../../javascript/reference/buffer-property-dataview.md)|只读。 获取此视图所引用的 ArrayBuffer。|  
|[byteLength 属性](../../javascript/reference/bytelength-property-dataview.md)|只读。 此视图从其 ArrayBuffer 开始的长度（以字节为单位），在构造时已固定。|  
|[byteOffset 属性](../../javascript/reference/byteoffset-property-dataview.md)|只读。 此视图从其 ArrayBuffer 开始的以字节为单位，如在构造时已固定偏移量。|  
  
## <a name="methods"></a>方法  
 下表列出了 `DataView` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[getInt8 方法](../../javascript/reference/getint8-method-dataview.md)|从开始处的视图中获取位于指定的字节偏移量处的 Int8 值。|  
|[getUint8 方法 (DataView)](../../javascript/reference/getuint8-method-dataview.md)|从开始处的视图中获取位于指定的字节偏移量处的 Uint8 值。|  
|[getInt16 方法 (DataView)](../../javascript/reference/getint16-method-dataview.md)|从开始处的视图，请在指定的字节偏移量中获取的 Int16 值。|  
|[getUint16 方法 (DataView)](../../javascript/reference/getuint16-method-dataview.md)|从开始处的视图中获取位于指定的字节偏移量处的 Uint16 值。|  
|[getInt32 方法 (DataView)](../../javascript/reference/getint32-method-dataview.md)|从开始处的视图中获取指定的字节偏移量处的 Int32 值。|  
|[getUint32 方法 (DataView)](../../javascript/reference/getuint32-method-dataview.md)|从开始处的视图，请在指定的字节偏移量中获取的 Uint32 值。|  
|[getFloat32 方法 (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|从开始处的视图中获取位于指定的字节偏移量处的 Float32 值。|  
|[getFloat64 方法 (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|从开始处的视图中获取位于指定的字节偏移量处的 Float64 值。|  
|[setInt8 方法 (DataView)](../../javascript/reference/setint8-method-dataview.md)|将指定的字节偏移量从视图的开始处 Int8 值存储。|  
|[setUint8 方法 (DataView)](../../javascript/reference/setuint8-method-dataview.md)|将指定的字节偏移量从视图的开始处 Uint8 值存储。|  
|[setInt16 方法 (DataView)](../../javascript/reference/setint16-method-dataview.md)|存储指定的字节偏移量从视图的开始处的 Int16 值。|  
|[setUint16 方法 (DataView)](../../javascript/reference/setuint16-method-dataview.md)|将指定的字节偏移量从视图的开始处 Uint16 值存储。|  
|[setInt32 方法 (DataView)](../../javascript/reference/setint32-method-dataview.md)|存储指定的字节偏移量从视图的开始处的 Int32 值。|  
|[setUint32 方法 (DataView)](../../javascript/reference/setuint32-method-dataview.md)|存储指定的字节偏移量从视图的开始处的 Uint32 值。|  
|[setFloat32 方法 (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|将指定的字节偏移量从视图的开始处 Float32 值存储。|  
|[setFloat64 方法 (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|将指定的字节偏移量从视图的开始处 Float64 值存储。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 DataView 对象处理从 XmlHttpRequest 获取的二进制数据：  
  
```JavaScript  
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
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]