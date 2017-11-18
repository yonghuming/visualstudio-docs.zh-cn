---
title: "splice 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>splice 方法 (Array) (JavaScript)
从一个数组中移除元素，如有必要，在所移除元素的位置上插入新元素，并返回所移除的元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 一个 `Array` 对象。  
  
 `start`  
 必需。 从其开始移除元素数组中从零开始的位置。  
  
 `deleteCount`  
 必需。 要移除的元素数。  
  
 `item1, item2,. . ., itemN`  
 可选。 要插入到代替所移除的元素数组的元素。  
  
## <a name="remarks"></a>备注  
 `splice`方法修改`arrayObj`通过从位置删除指定的数量的元素`start`并插入新元素。 所移除的元素返回作为新`Array`对象。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用 `splice` 方法。  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)