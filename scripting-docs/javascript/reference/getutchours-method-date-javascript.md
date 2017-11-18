---
title: "getUTCHours 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- UTC times, returning
- getUTCHours method
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34a07f9f63fe22d3101cc748e9dde978385a71ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutchours-method-date-javascript"></a>getUTCHours 方法 (Date) (JavaScript)
获取的小时值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回介于 0 和 23，该值指示午夜算起的小时数之间的整数。 如果时间为 1:00:00 am 之前，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下在一小时是 0 UTC 时间。 这一次可以为非零其他时区中。  
  
## <a name="remarks"></a>备注  
 若要获取的数小时午夜以来所经历使用本地时间，使用`getHours`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示 `getUTCHours` 方法的用法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getHours 方法 (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours 方法 (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 (Date)](../../javascript/reference/setutchours-method-date-javascript.md)