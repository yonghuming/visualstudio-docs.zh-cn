---
title: "ArrayBuffer 对象 |Microsoft 文档"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>ArrayBuffer 对象
表示二进制数据的原始缓冲区，可用于存储不同类型化数组的数据。 `ArrayBuffers`无法读取或写入到直接，但可传递给类型化数组或[DataView 对象](../../javascript/reference/dataview-object.md)来解释原始缓冲区，根据需要。  
  
 有关类型化数组的详细信息，请参阅[类型化数组](../../javascript/advanced/typed-arrays-javascript.md)。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>参数  
 `arrayBuffer`  
 必需。 `ArrayBuffer` 对象分配到的变量名称。  
  
 `length`  
 缓冲区的长度。 ArrayBuffer 的内容将初始化为 0。 如果无法分配请求数目的字节，则将引发异常。  
  
## <a name="properties"></a>属性  
 下表列出了 `ArrayBuffer` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[byteLength 属性](../../javascript/reference/bytelength-property-arraybuffer.md)|只读。 ArrayBuffer 的长度（以字节为单位）。|  
  
## <a name="functions"></a>函数  
 下表列出了 `ArrayBuffer` 对象的函数。  
  
|属性|描述|  
|--------------|-----------------|  
|[ArrayBuffer.isView 函数](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|确定对象是否提供缓冲区的视图。|  
  
## <a name="methods"></a>方法  
 下表列出了 `ArrayBuffer` 对象的方法。  
  
|属性|描述|  
|--------------|-----------------|  
|[slice 方法](../../javascript/reference/slice-method-arraybuffer.md)|返回 `ArrayBuffer` 的一部分。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 ArrayBuffer 对象处理从获取的二进制数据[XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx)。 你可以使用[DataView 对象](../../javascript/reference/dataview-object.md)获取单个值。  
  
```JavaScript  
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
  
## <a name="remarks"></a>备注  
 有关使用`XmlHttpRequest`，请参阅[XMLHttpRequest 增强功能](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069)。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]