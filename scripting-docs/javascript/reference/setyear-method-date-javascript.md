---
title: "setYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>setYear 方法 (Date) (JavaScript)
设置中的年份值`Date`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>参数  
 `dateObj`  
 必需。 任意 `Date` 对象。  
  
 `numYear`  
 必需。 对于 1900 到 1999 年，这将是数字值等于减去 1900 年。 对于该范围以外的日期，这将是 4 位数的数值。  
  
## <a name="remarks"></a>备注  
 此方法已过时，并保留它是为了向后兼容。 请改用 `setFullYear` 方法。  
  
 若要设置的年度`Date`对象到 1997，调用**setYear(97)**。 若要设置到 2010 年，调用**setYear(2010)**。 最后，若要设置为 0-99 的范围中每一年的年，使用`setFullYear`方法。  
  
> [!NOTE]
>  有关[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]版本 1.0，`setYear`使用一个值，是加上 1900 到提供的年份值的结果`numYear`，而不考虑的年份值。 例如，若要设置为 1899 年`numYear`为-1 并设置 2000 年`numYear`为 100。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getFullYear 方法 (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear 方法 (Date)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)