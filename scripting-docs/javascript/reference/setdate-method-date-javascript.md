---
title: "setDate 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>setDate 方法 (Date) (JavaScript)
设置的月天数值`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numDate`  
 必需。 一个等于每月天数的数值。  
  
## <a name="remarks"></a>备注  
 若要设置使用协调世界时 (UTC) 的月日期值，使用`setUTCDate`方法。  
  
 如果值`numDate`大于月份中的天数，日期将转移到更高版本的月份和/或年数。 例如，如果存储的日期是 1996 年 1 月 5 日和`setDate(32)`调用时，1996 年 2 月 1 日的日期更改。 如果`numDate`为负数，日期回滚到早期的月份和/或年。 例如，如果存储的日期是 1996 年 1 月 5 日和`setDate(-32)`调用时，对 1995 年 11 月 29 日的日期更改。  
  
 [SetFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)可以用来设置年、 月和每月天数。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `setDate` 方法。  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth 方法 (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)