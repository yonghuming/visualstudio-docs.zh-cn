---
title: "getYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>getYear 方法 (Date) (JavaScript)
获取的年份，该值`Date`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回年份。  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  此方法已过时，并提供有关向后兼容性。 请改用 `getFullYear` 方法。  
  
 在[!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]，然后在开始的 Internet Explorer 版本[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]，返回的值是减去 1900年所存储的年份。 例如，作为-1 返回 1899 年，并且作为 100 返回 2000 年。  
  
 在[!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)]通过[!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]，公式取决于在一年。 对于 1900 到 1999 年，返回的值是为所存储的年份减去 1900年的 2 位值。 对于该范围以外的日期，返回四位数年份。 例如，1996年返回为 96，但 1825年和 2025年原样返回。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getFullYear 方法 (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear 方法 (Date)](../../javascript/reference/setyear-method-date-javascript.md)