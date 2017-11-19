---
title: "reverse 方法 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>reverse 方法 (JavaScript)
反转中的元素`Array`。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 任意 `Array` 对象。  
  
## <a name="return-value"></a>返回值  
 反向的数组中。  
  
## <a name="remarks"></a>备注  
 所需`arrayObj`引用是`Array`对象。  
  
 `reverse`方法可反转的元素`Array`就地对象。 它不会创建一个新`Array`在执行期间的对象。  
  
 如果数组不是连续的`reverse`方法将创建填补数组中的数组中的元素。 具有值时创建的这些元素的每个`undefined`。  
  
## <a name="example"></a>示例  
 下面的示例演示 `reverse` 方法的用法。  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [concat 方法（数组）](../../javascript/reference/concat-method-array-javascript.md)