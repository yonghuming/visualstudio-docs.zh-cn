---
title: "setFullYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear 方法 (Date) (JavaScript)
设置的年`Date`对象使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numYear`  
 必需。 在一年一个数值。  
  
 `numMonth`  
 可选。 从零开始的月份 (0 表示年 1 月，11 十二月) 数字值。 如果必须指定`numDate`指定。  
  
 `numDate`  
 可选。 一个等于该月的一天的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选参数。 例如，如果`numMonth`自变量是可选的但未指定，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值**getMonth**方法。  
  
 此外，如果自变量的值大于其日历范围，或为负，则会汇总日期，向前或向后根据需要。  
  
 若要设置使用协调世界时 (UTC) 的年份，使用`setUTCFullYear`方法。  
  
 Date 对象中所支持的年份范围大约是 285616 年之前和之后 1970年。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`setFullYear`方法：  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getFullYear 方法 (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)