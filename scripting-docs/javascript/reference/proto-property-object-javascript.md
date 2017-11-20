---
title: "__proto__ 属性 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e38669c400acba6f4ed3c4ee3fb5836c31b1bc00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="proto-property-object-javascript"></a>__proto__属性 (Object) (JavaScript)
包含对指定的对象的内部原型的引用。  
  
## <a name="syntax"></a>语法  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>参数  
 `object`  
 必需。 在其上设置原型对象。  
  
## <a name="remarks"></a>备注  
 `__proto__`属性可以用于设置对象的原型。  
  
 对象或函数继承所有方法和属性的新原型，以及所有方法和新原型的原型链中的属性。 一个对象只能有仅单个原型 （不包括原型链的继承的原型），因此当你调用`__proto__`属性，替换以前的原型。  
  
 你可以仅在可扩展对象上设置的原型。 有关详细信息，请参阅[Object.preventExtensions 函数](../../javascript/reference/object-preventextensions-function-javascript.md)。  
  
> [!NOTE]
>  `__proto__`属性名称开始和结束带两个下划线。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何设置对象的原型。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何通过将属性添加到原型来将其添加到对象。  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>示例  
 下面的代码示例通过设置 `String` 对象上的新原型，将属性添加该对象上。  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [原型和原型继承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)