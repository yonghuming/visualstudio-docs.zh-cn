---
title: "toTimeString 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="totimestring-method-date-javascript"></a>toTimeString 方法 (Date) (JavaScript)
返回作为一个字符串值的时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>备注  
 所需 `objDate` 引用是 `Date` 对象。  
  
 `toTimeString`方法返回包含在当前时区的时间的字符串值。  
  
## <a name="example"></a>示例  
 在下面的示例中，在午夜 UTC，1970 年 1 月 1 日之后的时间设置为 2000年毫秒的值，然后写出。  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [toDateString 方法 (Date)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 (Date)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)