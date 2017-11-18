---
title: "split 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split 方法 (String) (JavaScript)
使用指定的分隔符将一个字符串拆分为多个子字符串，并将其以数组形式返回。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>参数  
 `stringObj`  
 必需。 要拆分的 `String` 对象或字符串。 此对象不会修改**拆分**方法。  
  
 `separator`  
 可选。 字符串或**正则表达式**标识字符或字符用于分隔字符串的对象。 如果忽略该参数，则将返回包含整个字符串的单元素数组。  
  
 `limit`  
 可选。 一个用于限制数组中返回的元素数量的值。  
  
## <a name="return-value"></a>返回值  
 结果**拆分**方法是每个位置分隔字符串的数组其中`separator`中发生`stringObj`。 `separator` 将不作为任何数组元素的一部分返回。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**拆分**方法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [concat 方法 （字符串）](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [滚动、 平移和缩放示例应用](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)