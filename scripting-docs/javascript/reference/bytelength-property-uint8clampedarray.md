---
title: "byteLength 属性 (Uint8ClampedArray) |Microsoft 文档"
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
ms.assetid: 37ae1728-8e2c-496c-bb77-f5f85b1ecbba
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a949f245b0710e4c44c7a5944869eca4ea146375
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-uint8clampedarray"></a>byteLength 属性 (Uint8ClampedArray)
只读。 此数组开始处的长度其[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)，以字节为单位，如在构造时已固定。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arrayByteLength = uint8ClampedArray.byteLength;  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组的长度。  
  
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
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray 对象](../../javascript/reference/uint8clampedarray-object-javascript.md)