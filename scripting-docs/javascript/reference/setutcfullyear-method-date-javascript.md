---
title: "setUTCFullYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear 方法 (Date) (JavaScript)
设置中的年份值`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numYear`  
 必需。 一个等于年份的数值。  
  
 `numMonth`  
 可选。 一个等于该月的数值。 年 1 月的值是 0，并且被连续遵循其他的月份值。 如果必须提供*numDate*提供。  
  
 *numDate*  
 可选。 一个等于每月天数的数值。  
  
## <a name="remarks"></a>备注  
 所有**设置**采用可选参数的方法使用从相应返回值**获取**方法，如果不指定可选的参数。 例如，如果`numMonth`未指定自变量，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]使用从返回的值`getUTCMonth`方法。  
  
 此外，如果自变量的值大于，其范围或是负的数字，其他存储的值都将进行相应修改。  
  
 若要设置使用本地时间的年份，使用`setFullYear`方法。  
  
 中支持的年份范围`Date`对象是任意一侧的 1970 年大约前后 285616。  
  
## <a name="example"></a>示例  
 下面的示例演示 `setUTCFullYear` 方法的用法。  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getFullYear 方法 (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)