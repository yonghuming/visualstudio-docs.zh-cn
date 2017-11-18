---
title: "sort 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>sort 方法 (Array) (JavaScript)
排序`Array`。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 任意 `Array` 对象。  
  
 `sortFunction`  
 可选。 用于确定元素的顺序的函数的名称。 如果省略，则对元素进行排序以升序，ASCII 字符。  
  
## <a name="return-value"></a>返回值  
 已排序的数组。  
  
## <a name="remarks"></a>备注  
 `sort`方法排序`Array`就地对象; 如果否新`Array`执行过程中创建对象。  
  
 如果提供中的函数`sortFunction`自变量，它必须返回下列值之一：  
  
-   负值传递的第一个自变量是否小于第二个参数。  
  
-   如果两个参数相等，则为零。  
  
-   如果第一个参数大于第二个参数是正数值。  
  
## <a name="example"></a>示例  
 下面的示例显示如何使用 `sort` 方法。  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]