---
title: "forEach 方法 (Map) (JavaScript) |Microsoft 文档"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d0ffa12b9a1995df14f4868872238cdc45b674a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-map-javascript"></a>forEach 方法 (Map) (JavaScript)
地图中每个元素执行指定的操作。  
  
## <a name="syntax"></a>语法  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>参数  
 `mapObj`  
 必需。 一个 `Map` 对象。  
  
 `callbackfn`  
 必需。 该函数的`forEach`映射中每个元素调用一次。 `callbackfn`接受最多三个自变量。 `forEach`调用`callbackfn`函数映射中每个元素的一次。  
  
 `thisArg`  
 可选。 一个对象，`this`关键字可引用在`callbackfn`函数。 如果省略 `thisArg`，则 `undefined` 将用作 `this` 值。  
  
## <a name="exceptions"></a>异常  
 如果 `callbackfn` 参数不是函数对象，则将引发 `TypeError` 异常。  
  
## <a name="remarks"></a>备注  
 回调函数的语法如下所示：  
  
 `function callbackfn(value, key, mapObj)`  
  
 下表中所示，可以通过使用最多三个参数，声明回调函数。  
  
|回调参数|定义|  
|-----------------------|----------------|  
|`value`|在映射中包含的值。|  
|`key`|在映射中包含的密钥。|  
|`mapObj`|`Map`要遍历对象。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何检索的成员`Map`使用`forEach`。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]