---
title: "subarray 方法 (Int32Array) |Microsoft 文档"
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
ms.assetid: deed3bd4-63cb-4ec8-b5d1-ce9ce4a38f54
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dac06eb850635c7e767fce07a25aeeb568196c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int32array"></a>subarray 方法 (Int32Array)
获取新的 Int32Array 视图的[ArrayBuffer 对象](../../javascript/reference/arraybuffer-object.md)存储为此数组，指定子数组的第一个和最后一个成员。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
var newInt32Array = int32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>参数  
 `newInt32Array`  
 此方法返回的子数组。  
  
 `begin`  
 数组开始处的索引。  
  
 `end`  
 数组结尾处的索引。 这是不包括在内的。  
  
## <a name="remarks"></a>备注  
 如果 `begin` 或 `end` 为负，则引用数组结尾处（而非数组开始处）的索引。 如果未指定 `end`，则子数组将包含类型化数组的从 `begin` 到结尾的所有元素。 `begin` 和 `end` 值指定的范围被限制到当前数组的有效索引范围。 如果新的类型化数组的计算长度为负，则会将其限制为零。 返回的数组与对其调用此方法的数组的类型相同。  
  
## <a name="example"></a>示例  
 以下示例演示如何获取一个长度为两个元素的子数组（从数组的第一个元素开始）。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Int32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]