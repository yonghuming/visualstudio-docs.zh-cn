---
title: "setMinutes 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>setMinutes 方法 (Date) (JavaScript)
设置中的分钟值**日期**对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMinutes`  
 必需。 一个等于分钟值的数值。 如果使用以下参数之一，则必须提供。  
  
 *numSeconds*  
 可选。 一个等于秒值的数值。 如果必须提供`numMilli`使用参数。  
  
 `numMilli`  
 可选。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果*numSeconds*参数未指定，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值`getSeconds`方法。  
  
 若要设置分钟值使用协调世界时 (UTC)，使用`setUTCMinutes`方法。  
  
 如果自变量的值大于其范围，或为负数，则会相应地修改其他存储的值。 例如，如果存储的日期是"1996 年 1 月 5 日 00:00:00"和**setMinutes(90)**是调用，日期更改为"1996 年 1 月 5 日 01:30:00。" 负数具有类似的行为。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setMinutes` 方法的用法。  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMinutes 方法 (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)