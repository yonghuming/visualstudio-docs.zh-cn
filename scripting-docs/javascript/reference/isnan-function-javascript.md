---
title: "isNaN 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>isNaN 函数 (JavaScript)
返回一个布尔值，该值指示某个值是否为保留值 `NaN`（非数字）。  
  
## <a name="syntax"></a>语法  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>返回值  
 如果转换为 `Number` 类型的值为 `NaN`，则为 `true`，否则为 `false`。  
  
## <a name="remarks"></a>备注  
 所需`numValue`是对其进行测试的值`NaN`。  
  
 通常使用此方法来测试 `parseInt` 和 `parseFloat` 方法的返回值。  
  
 或者，包含的变量`NaN`或无法与其自身比较另一个值。 如果它比较是不相等，则`NaN`。 这是因为`NaN`是唯一的值不等于其自身。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>示例  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>另请参阅  
 [isFinite 函数](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 常量](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 函数](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 函数](../../javascript/reference/parseint-function-javascript.md)