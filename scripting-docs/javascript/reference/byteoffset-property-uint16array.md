---
title: "byteOffset 属性 (Uint16Array) |Microsoft 文档"
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
ms.assetid: f7a97ea9-5f1d-466d-82cd-79fd8ab95771
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e2c45d6c9908d8dbeabf0ceb46516da4c745a3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-uint16array"></a>byteOffset 属性 (Uint16Array)
只读。 此数组与其 ArrayBuffer 开始处的偏移量（以字节为单位），在构造时已固定。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arrayOffset = uint16Array.byteOffset;  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取数组的偏移量。  
  
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
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]