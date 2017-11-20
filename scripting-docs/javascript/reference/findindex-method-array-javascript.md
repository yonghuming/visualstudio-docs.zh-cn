---
title: "findIndex 方法 (Array) (JavaScript) |Microsoft 文档"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="findindex-method-array-javascript"></a>findIndex 方法（数组）(JavaScript)
返回满足回调函数中指定的测试条件的第一个数组元素的索引值。  
  
## <a name="syntax"></a>语法  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 数组对象。  
  
 `callbackfn`  
 必需。 用于测试数组中的每个元素的回调函数。  
  
 `thisArg`  
 可选。 指定回调函数中的 `this` 对象。 如果未指定，则未定义 `this` 对象。  
  
## <a name="remarks"></a>备注  
 对于数组中的每个元素，`findIndex` 方法都会调用一次回调函数（采用升序索引顺序），直到有元素返回 `true`。 只要有一个元素返回 true，`findIndex` 立即返回该返回 true 的元素的索引值。 如果数组中没有任何元素返回 true，则 `findIndex` 返回 -1。  
  
 `findIndex` 不会改变数组对象。  
  
## <a name="callback-function-syntax"></a>回调函数语法  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, index, thisArg)`  
  
 你可使用最多三个参数来声明回调函数。  
  
 回调函数的参数如下所示。  
  
|回调参数|定义|  
|-----------------------|----------------|  
|`value`|数组元素的值。|  
|`index`|数组元素的数字索引。|  
|`arrayObj`|要遍历的数组对象。|  
  
## <a name="example"></a>示例  
 在下面的示例中，回调函数测试数组中的每个元素是否都等于 2。  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>示例  
 下面的示例使用箭头语法来测试每个元素。 在此示例中，没有任何元素返回 `true`，`findIndex` 返回 -1。  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]