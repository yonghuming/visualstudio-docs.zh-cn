---
title: "Math.acos 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos 函数 (JavaScript)
返回数字的反余弦值 （或反余弦值）。  
  
## <a name="syntax"></a>语法  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>参数  
 所需的 `number` 参数是数值表达式。  
  
## <a name="return-value"></a>返回值  
 反余弦值`number`自变量，以弧度为单位。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用 `acos` 函数。  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>备注  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Math.asin 函数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 对象](../../javascript/reference/math-object-javascript.md)