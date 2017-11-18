---
title: "getMinutes 方法 (Date) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>getMinutes 方法 (Date) (JavaScript)
获取的分钟数`Date`对象、 使用本地时间。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>参数  
 所需 `dateObj` 引用是 `Date` 对象。  
  
## <a name="return-value"></a>返回值  
 返回一个整数，介于 0 和 59 之间。 时间是小于一分钟在整点后，则返回零。 如果`Date`创建对象时未使用指定的时间，默认情况下的分钟值为 0。  
  
## <a name="remarks"></a>备注  
 若要获取使用协调世界时 (UTC) 的分钟值，请使用`getUTCMinutes`方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何`getMinutes`方法。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**： [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [getUTCMinutes 方法 (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)