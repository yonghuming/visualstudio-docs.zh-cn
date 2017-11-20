---
title: "setMonth 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth 方法 (Date) (JavaScript)
设置中的月份值`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMonth`  
 必需。 一个等于该月的数值。 年 1 月的值是 0，并且被连续遵循其他的月份值。  
  
 `dateVal`  
 可选。 表示每月的某一个数值。 如果未提供此值，通过调用值`getDate`使用方法。  
  
## <a name="remarks"></a>备注  
 若要设置月份值使用协调世界时 (UTC)，使用`setUTCMonth`方法。  
  
 如果值`numMonth`大于 11 （0 表示一月） 或为负数，相应地修改所存储的年份。 例如，如果所存储的日期是"1996 年 1 月 5 日"和**setMonth(14)**是调用，日期更改为"1997 年 3 月 5 日。"  
  
 **SetFullYear**方法可以用于设置年、 月和每月天数。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setMonth` 方法的用法。  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMonth 方法 (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth 方法 (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)