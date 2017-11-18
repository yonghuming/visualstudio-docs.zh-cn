---
title: "Date.UTC 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC 函数 (JavaScript)
返回自 1970 年 1 月 1 日午夜之间的毫秒数协调世界时 (UTC) （或格林威治标准时间） 和指定的日期。  
  
## <a name="syntax"></a>语法  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>参数  
 `year`  
 必需。 指定完整的年份是必需的跨世纪日期准确性。 如果`year`介于 0 和 99 之间使用，然后`year`被假定为 1900年 + `year`。  
  
 `month`  
 必需。 月份，介于 0 和 11 （一月到十二月） 之间的整数。  
  
 `day`  
 必需。 日期介于 1 和 31 之间的整数。  
  
 `hours`  
 可选。 如果必须提供`minutes`提供。 从 0 到 23 （午夜到晚上 11 点） 的整数，指定的小时。  
  
 `minutes`  
 可选。 如果必须提供`seconds`提供。 一个从 0 到 59 之间的整数，指定的分钟数。  
  
 `seconds`  
 可选。 如果必须提供`milliseconds`提供。 一个从 0 到 59 之间的整数，指定的秒数。  
  
 `ms`  
 可选。 一个从 0 到 999 之间的整数，指定毫秒数。  
  
## <a name="remarks"></a>备注  
 `Date.UTC`函数返回自 1970 年 1 月 1 日 UTC 午夜到所提供的日期之间的毫秒数。 此返回值可在`setTime`方法并在`Date`对象构造函数。 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果你指定 150 秒[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]重数定义为两个分 30 秒。  
  
 之间的差异`Date.UTC`函数和`Date`对象构造函数接受日期的在于`Date.UTC`函数假设 UTC，和`Date`对象构造函数采用本地时间。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Date.UTC` 函数的用法。  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [setTime 方法 (Date)](../../javascript/reference/settime-method-date-javascript.md)