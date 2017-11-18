---
title: "Date.now 函数 (JavaScript) |Microsoft 文档"
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
helpviewer_keywords: now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="datenow-function-javascript"></a>Date.now 函数 (JavaScript)
获取当前日期和时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>返回值  
 1970 年 1 月 1 日午夜的当前日期和时间之间的毫秒数。  
  
## <a name="remarks"></a>备注  
 [GetTime 方法](../../javascript/reference/gettime-method-date-javascript.md)返回之间的毫秒数 1970 年 1 月 1 日和指定的日期。  
  
 有关如何计算经过的时间和比较日期的信息，请参阅[计算日期和时间 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示 `now` 方法的用法。  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>要求  
 在已安装的版本早于不支持 Internet Explorer 9。 但是，在以下文档模式下支持： Quirks、 Internet Explorer 6 标准、 Internet Explorer 7 标准、 Internet Explorer 8 标准、 Internet Explorer 9 标准、 Internet Explorer 10 标准。 中也受支持[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用。  
  
## <a name="see-also"></a>另请参阅  
 [getTime 方法 (Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [计算日期和时间 (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)