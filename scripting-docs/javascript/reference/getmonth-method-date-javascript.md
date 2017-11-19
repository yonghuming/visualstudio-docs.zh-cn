---
title: "getMonth 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth 方法 (Date) (JavaScript)
获取使用本地时间的月份。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 `getMonth`方法返回一个整数，介于 0 （1 月） 和 11 （十二月） 之间。 有关`Date`构建需要"1996 年 1 月 5 日"，`getMonth`返回 0。  
  
## <a name="remarks"></a>备注  
 若要获取使用协调世界时 (UTC) 的月份值，请使用`getUTCMonth`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getMonth` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCMonth 方法 (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)