---
title: "valueOf 方法 (Date) |Microsoft 文档"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>valueOf 方法 (Date)
自午夜，UTC 1970 年 1 月 1 日以来以毫秒为单位返回存储的时间值。  
  
## <a name="syntax"></a>语法  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>参数  
 `date`对象是日期的任何实例。  
  
## <a name="return-value"></a>返回值  
 以 UTC 1970 年 1 月 1 日午夜算起的毫秒为单位存储的时间值。 这是相同的值`getTime`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`valueOf`日期的方法。  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]