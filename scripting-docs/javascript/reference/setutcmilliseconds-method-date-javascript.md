---
title: "setUTCMilliseconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmilliseconds-method-date-javascript"></a>setUTCMilliseconds 方法 (Date) (JavaScript)
设置毫秒值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMilli`  
 必需。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 若要设置使用本地时间的毫秒数，使用`setMilliseconds`方法。  
  
 如果的值`numMilli`大于 999，或为负数，秒 （和分钟、 小时数，以及等，如有必要） 存储的数将增加一个适当的数量。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setUTCMilliseconds` 方法的用法。  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMilliseconds 方法 (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)