---
title: "forEach 方法 (Set) (JavaScript) |Microsoft 文档"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>forEach 方法 (Set) (JavaScript)
一组中每个元素执行指定的操作。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>参数  
 `setObj`  
 必需。 一个 `Set` 对象。  
  
 `callbackfn`  
 必需。 `callbackfn`接受最多三个自变量。 该函数的`forEach`集中的每个元素调用一次。  
  
 `thisArg`  
 可选。 一个对象，`this`关键字可引用在`callbackfn`函数。 如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。  
  
## <a name="exceptions"></a>异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## <a name="remarks"></a>备注  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, key, setObj)`  
  
 下表中所示，可以通过使用最多三个参数，声明回调函数。  
  
|回调参数|定义|  
|-----------------------|----------------|  
|`value`|集中包含的值。|  
|`key`|集中包含的值。 一组有没有密钥，因此此值等同于`value`。|  
|`setObj`|`Set`要遍历对象。|  
  
## <a name="example"></a>示例  
 下面的示例说明如何使用 `forEach`。 `callbackfn`自变量包含回调函数的代码。  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>示例  
 下面的示例演示，你还可以检索成员从一组通过将一个参数传递给回调函数。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]