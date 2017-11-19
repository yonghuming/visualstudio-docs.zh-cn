---
title: "toISOString 方法 (Date) (JavaScript) |Microsoft 文档"
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
helpviewer_keywords: toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>toISOString 方法 (Date) (JavaScript)
返回采用 ISO 格式的日期为一个字符串值。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>返回值  
 标准化 (ISO) 格式的日期在国际组织中的字符串表示形式。  
  
## <a name="exceptions"></a>异常  
 如果`objDate`不包含有效的日期，`RangeError`引发异常。  
  
## <a name="remarks"></a>备注  
 ISO 格式为 ISO 8601 格式的简化形式。 有关详细信息，请参阅[日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)。  
  
 时区始终为 UTC，由后缀 Z 在输出中表示。  
  
## <a name="example"></a>示例  
 下面的示例演示 `toISOString` 方法的用法。  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [日期和时间字符串](../../javascript/date-and-time-strings-javascript.md)