---
title: "setHours 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>setHours 方法 (Date) (JavaScript)
设置中的小时值`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numHours`  
 必需。 一个等于小时值的数值。  
  
 `numMin`  
 可选。 一个等于分钟值的数值。 如果使用以下参数之一，则必须提供。  
  
 `numSec`  
 可选。 一个等于秒值的数值。 如果使用以下参数，则必须提供。  
  
 `numMilli`  
 可选。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果`numMinutes`未指定自变量，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值`getMinutes`方法。  
  
 若要设置小时值使用协调世界时 (UTC)，使用`setUTCHours`方法。  
  
 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00"，和**setHours(30)**是调用，日期更改为"1996 年 1 月 6 日 06:00:00。" 负数具有类似的行为。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setHours` 方法的用法。  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getHours 方法 (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours 方法 (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours 方法 (Date)](../../javascript/reference/setutchours-method-date-javascript.md)