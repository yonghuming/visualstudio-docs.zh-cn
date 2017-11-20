---
title: "format 属性 (Intl.DateTimeFormat) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intldatetimeformat"></a>format 属性 (Intl.DateTimeFormat)
返回一个函数，通过使用指定的日期/时间格式化程序设置格式的区域设置特定日期。  
  
## <a name="syntax"></a>语法  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>参数  
 `dateTimeFormatObj`  
 必需。 名称`DateTimeFormat`要用作格式化程序对象。  
  
## <a name="remarks"></a>备注  
 返回的函数`format`属性采用单个参数， `date`，并返回一个字符串，表示通过使用中指定的选项的本地化的日期`DateTimeFormat`对象。 `date`返回函数的参数必须是数字，而日期字符串或`Date`对象。 如果`date`未提供该函数使用[Date.now](../../javascript/reference/date-now-function-javascript.md)作为默认输入值。  
  
## <a name="example"></a>示例  
 下面的示例使用`DateTimeFormat`本地化为德语的日期"2007 年 12 月 1 日"和将其重新格式化的对象。  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Intl.DateTimeFormat 对象](../../javascript/reference/intl-datetimeformat-object-javascript.md)