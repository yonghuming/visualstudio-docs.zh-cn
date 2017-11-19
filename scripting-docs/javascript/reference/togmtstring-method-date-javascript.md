---
title: "toGMTString 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString 方法 (Date) (JavaScript)
返回转换为使用格林威治标准意味着 Time(GMT) 的字符串的日期。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>备注  
 所需`dateObj`引用可以是任何`Date`对象。  
  
 `toGMTString`方法已过时，并提供有关向后兼容。 建议你使用`toUTCString`方法相反。  
  
 `toGMTString`方法返回`String`对象包含的日期格式使用格林威治标准时间约定。 返回值的格式如下:"05 Jan 1996 00:00:00 GMT"。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toUTCString 方法 (Date)](../../javascript/reference/toutcstring-method-date-javascript.md)