---
title: "setMilliseconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setmilliseconds-method-date-javascript"></a>setMilliseconds 方法 (Date) (JavaScript)
设置毫秒值`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numMilli`  
 必需。 一个等于毫秒值的数值。  
  
## <a name="remarks"></a>备注  
 若要设置毫秒值使用协调世界时 (UTC)，使用`setUTCMilliseconds`方法。  
  
 如果值`numMilli`大于 999 或为负数，递增存储的秒数 （和分钟、 小时数，如有必要等） 合适数量。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setMilliseconds` 方法的用法。  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMilliseconds 方法 (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)