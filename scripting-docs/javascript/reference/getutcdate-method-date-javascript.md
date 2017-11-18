---
title: "getUTCDate 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDate method
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c38244e989027139329ae6aab762fd9fbabb3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcdate-method-date-javascript"></a>getUTCDate 方法 (Date) (JavaScript)
获取一天的月份，使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回介于 1 和表示天的-月份的 31 之间的整数。  
  
## <a name="remarks"></a>备注  
 若要获取使用本地时间每月天数，使用`getDate`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getUTCDate` 方法。  
  
```JavaScript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate 方法 (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)