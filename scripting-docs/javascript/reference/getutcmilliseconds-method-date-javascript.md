---
title: "getUTCMilliseconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds 方法 (Date) (JavaScript)
获取的毫秒数`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回从 0 到 999 的范围可以是毫秒值。  
  
## <a name="remarks"></a>备注  
 若要获取本地时间的毫秒数，使用`getMilliseconds`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示 `getUTCMilliseconds` 方法的用法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMilliseconds 方法 (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)