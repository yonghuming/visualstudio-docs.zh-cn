---
title: "setUTCDate 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate 方法 (Date) (JavaScript)
设置中每个月的数值天`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 *numDate*  
 必需。 一个等于每月天数的数值。  
  
## <a name="remarks"></a>备注  
 若要设置使用本地时间每月天数，使用`setDate`方法。  
  
 如果值*numDate*大于在存储在每月天数**日期**对象或为负数，则日期设置为日期等于*numDate*减在存储的每月天数。 例如，如果存储的日期是 1996 年 1 月 5 日，和**setutcdate （32)**调用时，1996 年 2 月 1 日的日期更改。 负数具有类似的行为。  
  
 **SetUTCFullYear**方法可以用于设置年、 月和每月天数。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setUTCDate` 方法的用法。  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate 方法 (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 (Date)](../../javascript/reference/setdate-method-date-javascript.md)