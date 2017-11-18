---
title: "getUTCSeconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds 方法 (Date) (JavaScript)
获取的秒数`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回一个整数，介于 0 和 59 之间。 当时间少于一秒到当前分钟，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下，UTC 秒值为 0。  
  
## <a name="remarks"></a>备注  
 若要获取本地时间的秒数，使用`getSeconds`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getUTCSeconds` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getSeconds 方法 (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds 方法 (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)