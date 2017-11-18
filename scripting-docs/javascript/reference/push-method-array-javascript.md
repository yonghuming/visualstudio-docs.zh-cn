---
title: "push 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="push-method-array-javascript"></a>push 方法 (Array) (JavaScript)
将新元素追加到一个数组中，并返回数组的新长度。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>参数  
 `arrayObj`  
 必需。 一个 `Array` 对象。  
  
 `item, item2,. . ., itemN`  
 可选。 新元素的`Array`。  
  
## <a name="remarks"></a>备注  
 `push`和`pop`方法，你可以模拟后进先出堆栈。  
  
 `push`方法将它们的出现顺序的元素追加。 如果自变量之一是一个数组，则将它添加为作为单个元素。 使用`concat`方法来合并来自两个或多个数组元素。  
  
## <a name="example"></a>示例  
 下面的示例演示 `push` 方法的用法。  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [concat 方法 (Array)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop 方法 (Array)](../../javascript/reference/pop-method-array-javascript.md)