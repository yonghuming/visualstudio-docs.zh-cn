---
title: "slice 方法 (ArrayBuffer) |Microsoft 文档"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-arraybuffer"></a>slice 方法 (ArrayBuffer)
返回某一部分[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## <a name="syntax"></a>语法  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>参数  
 `arrayBufferObj`  
 必需。 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)部分将从复制的对象。  
  
 `start`  
 必需。 要复制的开头部分的字节索引。  
  
 `end`  
 可选。 要复制的结尾部分的字节索引。  
  
## <a name="remarks"></a>备注  
 `slice`方法返回[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)对象，其中包含的指定的部分`arrayBufferObj`。  
  
 `slice` 方法可以复制最多（但不包括） `end` 指示的字节。 如果`start`或`end`为负，指定的索引将被视为`length`  +  `start`或`end`分别，其中`length`的长度是[ArrayBuffer](../../javascript/reference/arraybuffer-object.md). 如果省略了 `end`，将继续提取，直到 `arrayBufferObj` 的结尾。 如果`end`之前发生`start`，任何字节复制到新[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `slice` 方法。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)