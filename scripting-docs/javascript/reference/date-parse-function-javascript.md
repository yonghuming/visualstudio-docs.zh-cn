---
title: "Date.parse 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="dateparse-function-javascript"></a>Date.parse 函数 (JavaScript)
分析包含日期的字符串并返回该日期和 1970 年 1 月 1 日午夜之间的毫秒数。  
  
## <a name="syntax"></a>语法  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>备注  
 所需`dateVal`自变量是一个任一包含日期或从某个 ActiveX 对象或其他对象中检索一个 VT_DATE 值的字符串。 有关日期信息字符串为`Date.parse`函数可以分析。 请参阅[日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)。  
  
 `Date.parse`函数返回一个整数值，表示 1970 年 1 月 1 日午夜和中提供的日期之间的毫秒数`dateVal`。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `Date.parse` 函数的用法。  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>示例  
 下面的示例返回日期提供与 1970 年 1 月 1 日之间的差异。  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)