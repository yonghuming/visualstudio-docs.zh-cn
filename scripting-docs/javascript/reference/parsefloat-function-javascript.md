---
title: "parseFloat 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat 函数 (JavaScript)
将字符串转换为浮点数。  
  
## <a name="syntax"></a>语法  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>备注  
 所需`numString`自变量是包含浮点数的字符串。  
  
 `parseFloat`函数返回一个数字值等于中包含的数字`numString`。 如果没有前缀`numString`可以成功解析为浮点数，`NaN`返回 （而不是数字）。  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 你可以测试`NaN`使用`isNaN`函数。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 函数](../../javascript/reference/parseint-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)