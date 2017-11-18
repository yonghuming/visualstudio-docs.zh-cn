---
title: "getUTCDay 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDay method
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee9953a7abf548ef15cc124e09b914af360ca23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcday-method-date-javascript"></a>getUTCDay 方法 (Date) (JavaScript)
获取使用协调世界时 (UTC) 星期几。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回介于 0 （星期日） 和 6 （星期六），表示一周中的日期之间的整数。  
  
## <a name="remarks"></a>备注  
 若要获取使用本地时间星期几，使用`getDate`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getUTCDay` 方法。  
  
```JavaScript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getDay 方法 (Date)](../../javascript/reference/getday-method-date-javascript.md)