---
title: "getUTCMonth 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC dates, returning
- Month method
- getUTCMonth method
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07e7ecdc9a9ee8a49c12fc65e4b2ba1056bd377c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmonth-method-date-javascript"></a>getUTCMonth 方法 (Date) (JavaScript)
获取的月份`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回一个整数，介于 0 （1 月） 和 11 （十二月） 之间。  
  
## <a name="remarks"></a>备注  
 若要获取本地时间的月份，使用**getMonth**方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getUTCMonth` 方法。  
  
```JavaScript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMonth 方法 (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth 方法 (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)