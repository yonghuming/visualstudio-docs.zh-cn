---
title: "prototype 属性 （日期） |Microsoft 文档"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-date"></a>prototype 属性（日期）
日期返回对原型的引用。  
  
## <a name="syntax"></a>语法  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>备注  
 `date` 参数是对象的名称。  
  
 使用`prototype`属性来提供到日期的一组基本的功能。 对象的新实例“继承”了分配给该对象的原型的行为。  
  
 例如，要将方法添加到返回数组的最大元素值的 `Date` 对象，请声明该函数，将其添加至 `Date.prototype`，然后再使用它。  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象具有`prototype`属性是只读的。 属性和方法可能添加至原型，但该对象可能无法为指定其他原型。 但是，可能将用户定义的对象分配的新原型。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]