---
title: "pop 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>pop 方法 (Array) (JavaScript)
从数组中移除最后一个元素并将该元素返回。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>备注  
 [推送](../../javascript/reference/push-method-array-javascript.md)和`pop`方法使你能够模拟的堆栈，使用后进先出 (LIFO) 来存储数据的原则。  
  
 所需`arrayObj`引用是`Array`对象。  
  
 如果数组为空，`undefined`返回。  
  
## <a name="example"></a>示例  
 下面的示例演示 `pop` 方法的用法。  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [push 方法 (Array)](../../javascript/reference/push-method-array-javascript.md)