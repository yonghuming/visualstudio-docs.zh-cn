---
title: "setSeconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>setSeconds 方法 (Date) (JavaScript)
设置秒值`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 *numSeconds*  
 必需。 一个等于秒值的数值。  
  
 `numMilli`  
 可选。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果`numMilli`未指定自变量，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值**getMilliseconds**方法。  
  
 若要设置秒值使用协调世界时 (UTC)，使用`setUTCSeconds`方法。  
  
 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00"和**setSeconds(150)**是调用，日期更改为"1996 年 1 月 5 日 00:02:30。"  
  
 `setHours`方法可以用于设置小时、 分钟、 秒和毫秒。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setSeconds` 方法的用法。  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getSeconds 方法 (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)