---
title: "BYTES_PER_ELEMENT 常量 (Uint8ClampedArray) |Microsoft 文档"
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
ms.assetid: f9fb2a10-9faf-4534-9183-dad2984e74ff
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c230696fa7e1ea8c650b92a157461c6054419824
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bytesperelement-constant-uint8clampedarray"></a>BYTES_PER_ELEMENT 常量 (Uint8ClampedArray)
数组中每个元素的大小（以字节为单位）。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arraySize = uint8ClampedArray.BYTES_PER_ELEMENT;  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组元素的大小。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)