---
title: "unshift 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>unshift 方法 (Array) (JavaScript)
在数组的开头插入新元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 一个 `Array` 对象。  
  
 `item1, item2,. . ., itemN`  
 可选。 要插入的开头元素`Array`。  
  
## <a name="remarks"></a>备注  
 `unshift`方法将元素插入到数组的开头，所以它们出现在参数列表中显示的顺序相同。  
  
## <a name="example"></a>示例  
 下面的示例演示 `unshift` 方法的用法。  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [shift 方法 (Array)](../../javascript/reference/shift-method-array-javascript.md)