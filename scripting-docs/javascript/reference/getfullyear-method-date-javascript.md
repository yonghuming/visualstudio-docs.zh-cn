---
title: "getFullYear 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear 方法 (Date) (JavaScript)
获取一年中，使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 由四位数字表示的年份。 例如，年份 1976年被返回值为 1976年。 指定为两个数字中的年`Date`构造函数或在`setFullYear`假定处于二十世纪，因此给定"5/14/12"`getFullYear`返回"公历 1912"。  
  
## <a name="remarks"></a>备注  
 若要获取使用协调世界时 (UTC) 的年份，使用`getUTCFullYear`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**getFullYear**方法。  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCFullYear 方法 (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)