---
title: "setUint8 方法 (DataView) |Microsoft 文档"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ab533520d933b11657175d396433d732536c7a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setuint8-method-dataview"></a>setUint8 方法 (DataView)
将指定的字节偏移量从视图的开始处 Uint8 值存储。  
  
## <a name="syntax"></a>语法  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## <a name="parameters"></a>参数  
 `byteOffset`  
 应在其中设置的值的缓冲区中的位置。  
  
 `value`  
 要设置的值。  
  
## <a name="remarks"></a>备注  
 如果他们将编写视图的结尾之外，这些方法将引发异常。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置第一个 Uint8 处于数据视图。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]