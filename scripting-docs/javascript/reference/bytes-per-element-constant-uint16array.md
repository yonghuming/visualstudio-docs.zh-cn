---
title: "BYTES_PER_ELEMENT 常量 (Uint16Array) |Microsoft 文档"
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
ms.assetid: 4e5e8a70-f8b9-4e3c-b9f3-0d1249963c28
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a437564d98120a74e43df81670ade92dadba792
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="bytesperelement-constant-uint16array"></a>BYTES_PER_ELEMENT 常量 (Uint16Array)
数组中每个元素的大小（以字节为单位）。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arraySize = uint16Array.BYTES_PER_ELEMENT;  
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
            var intArr = new Uint16Array(buffer.byteLength / 2);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]