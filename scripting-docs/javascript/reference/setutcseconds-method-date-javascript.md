---
title: "setUTCSeconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcseconds-method-date-javascript"></a>setUTCSeconds 方法 (Date) (JavaScript)
设置秒值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 *numSeconds*  
 必需。 一个等于秒值的数值。  
  
 `numMilli`  
 可选。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果`numMilli`未指定自变量，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值`getUTCMilliseconds`方法。  
  
 若要设置秒值使用本地时间，使用`setSeconds`方法。  
  
 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00.00"和**setSeconds(150)**是调用，日期更改为"1996 年 1 月 5 日 00:02:30.00。"  
  
 **SetUTCHours**方法可以用于设置小时、 分钟、 秒和毫秒。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setUTCSeconds` 方法的用法。  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getSeconds 方法 (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 (Date)](../../javascript/reference/setseconds-method-date-javascript.md)