---
title: "setUTCMonth 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth 方法 (Date) (JavaScript)
设置中的月份值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMonth`  
 必需。 一个等于该月的数值。 年 1 月的值是 0，并且被连续遵循其他的月份值。  
  
 `dateVal`  
 可选。 表示每月的某一个数值。 如果未提供，通过调用值`getUTCDate`使用方法。  
  
## <a name="remarks"></a>备注  
 若要设置使用本地时间的月份值，使用`setMonth`方法。  
  
 如果值`numMonth`大于 11 （年 1 月是月份 0），或为负数，所存储的年份适当地是递增或递减。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00.00"和**setUTCMonth(14)**是调用，日期更改为"1997 年 3 月 5 日 00:00:00.00。"  
  
 **SetUTCFullYear**方法可以用于设置年、 月和每月天数。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setUTCMonth` 方法的用法。  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMonth 方法 (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 (Date)](../../javascript/reference/setmonth-method-date-javascript.md)