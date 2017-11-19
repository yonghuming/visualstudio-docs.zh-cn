---
title: "getDate 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, returning day of the month
- getDate method
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfb3a8ad3ba433dc776f0831d1eac4787b8aea90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getdate-method-date-javascript"></a>getDate 方法 (Date) (JavaScript)
获取一天的月份，使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getDate()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 一个介于 1 和 31 之间的整数，表示天的月份。  
  
## <a name="remarks"></a>备注  
 若要获取一天的月中的使用通用协调时间 (UTC)，请使用`getUTCDate`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示 `getDate` 方法的用法。  
  
```JavaScript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCDate 方法 (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)