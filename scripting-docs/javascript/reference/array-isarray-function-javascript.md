---
title: "Array.isArray 函数 (JavaScript) |Microsoft 文档"
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
helpviewer_keywords:
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arrayisarray-function-javascript"></a>Array.isArray 函数 (JavaScript)
确定对象是否为数组。  
  
## <a name="syntax"></a>语法  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 要测试的对象。  
  
## <a name="return-value"></a>返回值  
 如果 `object` 是数组，则为 `true`；否则为 `false`。 如果 `object` 参数不是对象，则返回 `false`。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Array.isArray` 函数的用法。  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 运算符](../../javascript/reference/typeof-operator-decrementjavascript.md)