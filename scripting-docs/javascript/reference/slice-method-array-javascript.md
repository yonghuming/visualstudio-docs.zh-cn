---
title: "slice 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice 方法 (Array) (JavaScript)
返回一个数组中的一部分。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 一个 `Array` 对象。  
  
 `start`  
 必需。 指定部分的开头`arrayObj`。  
  
 `end`  
 可选。 指定部分的末尾`arrayObj`。  
  
## <a name="remarks"></a>备注  
 `slice`方法返回`Array`对象，其中包含的指定的部分`arrayObj`。  
  
 `slice`方法复制到，但不是包括，指示元素`end`。 如果`start`是负数，它将被视为`length`  +  `start`，其中`length`是数组的长度。 如果`end`是负数，它将被视为`length`  +  `end`其中`length`是数组的长度。 如果省略了 `end`，将继续提取，直到 `arrayObj` 的结尾。 如果`end`之前发生`start`，没有元素被复制到新数组。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 `slice` 方法。 在第一个示例中，除最后一个元素的`myArray`复制到`newArray`。 在第二个示例中，只有最后两个元素的`myArray`复制到`newArray`。  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [slice 方法 （字符串）](../../javascript/reference/slice-method-string-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)