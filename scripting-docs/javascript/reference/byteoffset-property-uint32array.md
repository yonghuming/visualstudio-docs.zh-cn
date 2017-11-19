---
title: "byteOffset 属性 (UInt32Array) |Microsoft 文档"
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
ms.assetid: 61b1b117-e197-4655-b487-97d08c098775
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af7bf875d32e4db457c00789b84a42f16fa2b30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-uint32array"></a>byteOffset 属性 (UInt32Array)
只读。 此数组与其 ArrayBuffer 开始处的偏移量（以字节为单位），在构造时已固定。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var arrayOffset = uint32Array.byteOffset;  
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
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]