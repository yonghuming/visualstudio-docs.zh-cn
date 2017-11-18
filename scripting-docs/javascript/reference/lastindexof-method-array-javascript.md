---
title: "lastIndexOf 方法 (Array) (JavaScript) |Microsoft 文档"
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf 方法 (Array) (JavaScript)
返回指定值在数组中的最后一个匹配项的索引。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|定义|  
|---------------|----------------|  
|`array1`|必需。 要搜索的数组对象。|  
|`searchElement`|必需。 要查找中的值`array1`。|  
|`fromIndex`|可选。 的数组索引处开始搜索。 如果`fromIndex`是省略，则为数组中的最后一个索引处开始搜索。|  
  
## <a name="return-value"></a>返回值  
 最后一个匹配项的索引`searchElement`中的数组，或者，则为-1`searchElement`找不到。  
  
## <a name="remarks"></a>备注  
 `lastIndexOf`方法搜索指定的值的数组。 如果找不到指定的值，此方法将返回第一个匹配项，则为-1 的索引。  
  
 搜索发生降序索引 （姓氏成员名字）。 若要搜索升序排序，请使用[indexOf 方法 （数组）](../../javascript/reference/indexof-method-array-javascript.md)。  
  
 与数组元素进行比较`searchElement`严格的相等性，类似于所做的比较值`===`运算符。 有关详细信息，请参阅[比较运算符](../../javascript/reference/comparison-operators-javascript.md)。  
  
 可选`fromIndex`参数指定的数组索引处开始搜索。 如果`fromIndex`大于或等于数组长度，则会搜索整个数组。 如果`fromIndex`为负，搜索从处开始的数组长度加号`fromIndex`。 如果计算的索引小于 0，则返回-1。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`lastIndexOf`方法。  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [indexOf 方法 (Array)](../../javascript/reference/indexof-method-array-javascript.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)