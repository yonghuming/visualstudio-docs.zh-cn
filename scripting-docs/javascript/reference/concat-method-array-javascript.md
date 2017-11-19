---
title: "concat 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat 方法 (Array) (JavaScript)
将两个或多个数组合并。  
  
## <a name="syntax"></a>语法  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>参数  
 `array1`  
 必需。 `Array`对象转换为其他数组串联。  
  
 `item1,. . ., itemN`  
 可选。 要添加到末尾的其他项`array1`。  
  
## <a name="remarks"></a>备注  
 `concat`方法返回`Array`对象，其中包含的串联`array1`和提供的任何其他项。  
  
 要添加的项 (*item1 itemN*) 到数组，按顺序添加，从列表中的第一个项。 如果某一项是一个数组，其内容将添加到末尾`array1`。 如果数组以外的任何项，它是作为添加到数组末尾之间的单个数组元素。  
  
 源数组的元素复制到生成的数组，如下所示：  
  
-   如果从任何连接到新数组的数组复制对象，对象引用将继续指向相同的对象。 新数组或原始数组中的更改将会另一项更改。  
  
-   如果一个数字或字符串的值添加到新数组，则仅该值被复制。 更改一个数组中的值不会影响另一部分中的值。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`concat`方法与数组一起使用时：  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [concat 方法 （字符串）](../../javascript/reference/concat-method-string-javascript.md)   
 [join 方法 (Array)](../../javascript/reference/join-method-array-javascript.md)