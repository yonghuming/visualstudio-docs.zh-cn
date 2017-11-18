---
title: "Array.of 函数 （数组） (JavaScript) |Microsoft 文档"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="arrayof-function-array-javascript"></a>Array.of 函数（数组）(JavaScript)
从传入的自变量返回一个数组。  
  
## <a name="syntax"></a>语法  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>参数  
 `element0,...,elementN`  
 可选。 要置于数组中的元素。 这将创建一个具有 n + 1 个元素且长度为 n + 1 的数组。  
  
## <a name="remarks"></a>备注  
 此函数类似于调用 `new Array(args)`，但当传入一个参数时，`Array.of` 不包括特殊行为。  
  
## <a name="example"></a>示例  
 下面的示例基于传入的数字创建一个数组。  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>示例  
 下面的示例演示使用 `Array.of` 与 `new Array` 之间的差异。  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]