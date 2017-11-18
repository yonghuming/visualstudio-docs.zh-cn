---
title: "toUTCString 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="toutcstring-method-date-javascript"></a>toUTCString 方法 (Date) (JavaScript)
返回的日期转换为使用协调世界时 (UTC) 的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>备注  
 所需`dateObj`引用可以是任何`Date`对象。  
  
 `toUTCString`方法返回`String`对象，其中包含以一种方便使用 UTC 约定进行格式化的日期易读的形式。  
  
## <a name="example"></a>示例  
 下面的示例演示 `toUTCString` 方法的用法。  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toGMTString 方法 (Date)](../../javascript/reference/togmtstring-method-date-javascript.md)