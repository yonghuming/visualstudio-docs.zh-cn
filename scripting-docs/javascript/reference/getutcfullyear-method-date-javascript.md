---
title: "getUTCFullYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear 方法 (Date) (JavaScript)
获取使用协调世界时 (UTC) 的年份。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回的四位数字表示的年份。 指定为两个数字中的年`Date`构造函数或在`setFullYear`假定处于二十世纪，因此给定"5/14/12"`getUTCFullYear`返回"公历 1912"。  
  
## <a name="remarks"></a>备注  
 若要获取使用本地时间的年份，使用`getFullYear`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getUTCFullYear` 方法。  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getFullYear 方法 (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)