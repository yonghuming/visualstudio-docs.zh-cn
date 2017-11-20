---
title: "getUTCMinutes 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes 方法 (Date) (JavaScript)
获取的分钟数`Date`对象使用协调世界时 (UTC)。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回一个整数，介于 0 和 59 之间。 时间是小于一分钟在整点后，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下，UTC 分钟值为 0。 但是，在其他时区可能不同。  
  
## <a name="remarks"></a>备注  
 若要获取的存储使用本地时间的分钟数，请使用`getMinutes`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示 `getUTCMinutes` 方法的用法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getMinutes 方法 (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes 方法 (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)