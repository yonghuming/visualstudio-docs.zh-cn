---
title: "Math.hypot 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathhypot-function-javascript"></a>Math.hypot 函数 (JavaScript)
返回自变量平方和的平方根。  
  
## <a name="syntax"></a>语法  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>参数  
 `value1`  
 必需。 第一个数字。  
  
 `value2`  
 可选。 第二个数字。  
  
 `values`  
 可选。 一个或多个数字。  
  
## <a name="remarks"></a>备注  
 如果有任意自变量为 NaN，则该函数返回 NaN。 如果未提供任何自变量，则该函数返回 0。  
  
## <a name="example"></a>示例  
 下面的示例演示一个使用 `Math.hypot` 函数的示例。  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]