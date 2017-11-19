---
title: "setUTCMinutes 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes 方法 (Date) (JavaScript)
设置中的分钟值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMinutes`  
 必需。 一个等于分钟值的数值。 如果使用以下参数之一，则必须提供。  
  
 *numSeconds*  
 可选。 一个等于秒值的数值。 如果必须提供`numMilli`使用。  
  
 `numMilli`  
 可选。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果*numSeconds*未指定自变量，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值`getUTCSeconds`方法。  
  
 若要修改使用本地时间的分钟值，使用`setMinutes`方法。  
  
 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00.00"和**setUTCMinutes(70)**是调用，日期更改为"1996 年 1 月 5 日 01:10:00.00。"  
  
 **SetUTCHours**方法可以用于设置小时、 分钟、 秒和毫秒。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`setUTCMinutes`方法：  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMinutes 方法 (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 (Date)](../../javascript/reference/setminutes-method-date-javascript.md)