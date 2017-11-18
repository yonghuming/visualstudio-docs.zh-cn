---
title: "getUint8 方法 (DataView) |Microsoft 文档"
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 315baa2ca5abfe006a7f8d524619479d99a11fc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getuint8-method-dataview"></a>getUint8 方法 (DataView)
从开始处的视图中获取位于指定的字节偏移量处的 Uint8 值。 没有任何对齐约束;可从任何偏移量读取多字节值。  
  
## <a name="syntax"></a>语法  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## <a name="parameters"></a>参数  
 `testInt`  
 必需。 从方法返回 Uint8 值。  
  
 `byteOffset`  
 应从该处检索的值的缓冲区中的位置。  
  
## <a name="remarks"></a>备注  
 如果它们将读取超出末尾的视图，这些方法将引发异常。  
  
## <a name="example"></a>示例  
 下面的示例演示如何获取第一个 Uint8 处于数据视图。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]