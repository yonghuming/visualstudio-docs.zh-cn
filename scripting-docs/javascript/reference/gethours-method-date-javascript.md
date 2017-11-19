---
title: "getHours 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>getHours 方法 (Date) (JavaScript)
获取小时数日期，以使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 指示午夜算起的小时数介于 0 和 23 之间的整数。 如果时间为 1:00:00 am 之前，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下小时为 0。  
  
## <a name="remarks"></a>备注  
 若要获取使用协调世界时 (UTC) 的小时值，请使用`getUTCHours`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getHours` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCHours 方法 (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 (Date)](../../javascript/reference/setutchours-method-date-javascript.md)