---
title: "getSeconds 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getseconds-method-date-javascript"></a>getSeconds 方法 (Date) (JavaScript)
获取的秒数`Date`对象、 使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回一个整数，介于 0 和 59 之间。 当时间少于一秒到当前分钟，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下则秒值为 0。  
  
## <a name="remarks"></a>备注  
 若要获取秒的值使用协调世界时 (UTC)，请使用`getUTCSeconds`方法。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `getSeconds` 方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCSeconds 方法 (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)