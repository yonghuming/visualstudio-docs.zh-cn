---
title: "setTime 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>setTime 方法 (Date) (JavaScript)
设置日期和时间值以`Date`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 *毫秒*  
 必需。 格林威治标准时间 1970 年 1 月 1 日午夜以来表示已用的毫秒数的数字值。  
  
## <a name="remarks"></a>备注  
 如果*毫秒*是负数，它指示早于 1970 年的日期。 可用的日期范围是 1970年的从任意一侧大约 285616 年。  
  
 设置的日期和时间与`setTime`方法无关的时区。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setTime` 方法的用法。  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getTime 方法 (Date)](../../javascript/reference/gettime-method-date-javascript.md)