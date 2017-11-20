---
title: "parseInt 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt 函数 (JavaScript)
将字符串转换为整数。  
  
## <a name="syntax"></a>语法  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>参数  
 `numString`  
 必需。 要将转换为数字的字符串。  
  
 `radix`  
 可选。 介于 2 和 36 指定中数字的基数的`numString`。 如果未提供此参数，以"0x"前缀的字符串视为十六进制。 所有其他字符串都被视为是十进制的。  
  
## <a name="remarks"></a>备注  
 `parseInt`函数返回一个整数值等于中包含的数字`numString`。 如果没有前缀`numString`可以转换为整数，成功分析`NaN`返回 （而不是数字）。  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 你可以测试`NaN`使用`isNaN`函数。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  从开始[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]、`parseInt`函数不会将其"0"为八进制前缀的字符串。 不使用时`parseInt`函数中，但是，前缀为"0"的字符串可以仍解释为 octals。 请参阅[数据类型](../../javascript/data-types-javascript.md)有关八进制整数。  
  
## <a name="see-also"></a>另请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 函数](../../javascript/reference/parsefloat-function-javascript.md)   
 [字符串对象](../../javascript/reference/string-object-javascript.md)   
 [valueOf 方法 (Object)](../../javascript/reference/valueof-method-object-javascript.md)