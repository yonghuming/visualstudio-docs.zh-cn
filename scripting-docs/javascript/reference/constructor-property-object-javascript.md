---
title: "constructor 属性 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-object-javascript"></a>constructor 属性（对象）(JavaScript)
指定用于创建对象的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>备注  
 所需`object`是对象或函数的名称。  
  
 `constructor` 属性是具有原型的每个对象的原型的成员。 这包括所有内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象除外`Global`和`Math`对象。 `constructor` 属性包含对构造特定对象实例的函数的引用。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用构造函数属性。  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [prototype 属性 (Object)](../../javascript/reference/prototype-property-object-javascript.md)