---
title: "indexOf 方法 (Array) (JavaScript) |Microsoft 文档"
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
helpviewer_keywords:
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-array-javascript"></a>indexOf 方法 (Array) (JavaScript)
返回某个值在数组中的第一个匹配项的索引。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 一个数组对象。|  
|`searchElement`|必需。 要查找中的值`array1`。|  
|`fromIndex`|可选。 的数组索引处开始搜索。 如果`fromIndex`是省略，位于索引 0 处开始搜索。|  
  
## <a name="return-value"></a>返回值  
 第一个匹配项的索引`searchElement`中的数组，或者，则为-1`searchElement`找不到。  
  
## <a name="remarks"></a>备注  
 `indexOf`方法搜索指定的值的数组。 如果找不到指定的值，此方法将返回第一个匹配项，则为-1 的索引。  
  
 搜索发生采用升序索引顺序。  
  
 与数组元素进行比较`searchElement`值按严格式，类似于`===`运算符。 有关详细信息，请参阅[比较运算符](../../javascript/reference/comparison-operators-javascript.md)。  
  
 可选`fromIndex`参数指定的数组索引处开始搜索。 如果`fromIndex`大于或等于数组长度，则返回-1。 如果`fromIndex`为负，搜索从处开始的数组长度加号`fromIndex`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`indexOf`方法。  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)