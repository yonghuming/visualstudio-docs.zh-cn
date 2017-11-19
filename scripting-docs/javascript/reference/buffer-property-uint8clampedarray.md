---
title: "buffer 属性 (Uint8ClampedArray) |Microsoft 文档"
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
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a16ee962b3d8dcdbd99eb10b5870f3564ba351d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="buffer-property-uint8clampedarray"></a>buffer 属性 (Uint8ClampedArray)
只读。 获取[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)此数组引用。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组的 ArrayBuffer。  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)