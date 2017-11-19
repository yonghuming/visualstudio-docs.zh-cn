---
title: "符号对象 (JavaScript) |Microsoft 文档"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="symbol-object-javascript"></a>符号对象 (JavaScript)
允许你创建唯一标识符。  
  
## <a name="syntax"></a>语法  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>参数  
 `desc`  
 可选。 符号说明。  
  
## <a name="remarks"></a>备注  
 符号对象允许将属性添加到现有对象，而不可能干扰现有对象属性、不存在任何意外的可见性并且不存在其他代码进行的任何其他不协调的添加。  
  
 符号是基元数据类型。 不能使用 `new` 运算符创建符号对象。  
  
 要将符号对象添加到全局符号注册表，使用 `Symbol.for` 和 `Symbol.keyFor` 函数。 如果将符号序列化为字符串形式，则使用全局符号注册表，以确保针对所有查找项，特定字符串映射到正确符号。  
  
 JavaScript 包括以下可在全局范围中使用的内置符号值。  
  
|符号|描述|  
|------------|-----------------|  
|`Symbol.hasInstance`|此方法可确定是否构造函数会将对象识别为构造函数的实例之一。 它由 `instanceof` 运算符在内部使用。|  
|`Symbol.isConcatSpreadable`|此属性返回一个布尔值，该值指示是否应通过 `Array.concat` 将对象平展至其数组元素。|  
|`Symbol.iterator`|此方法返回对象的默认迭代器。 它由 `for...of` 语句在内部使用。|  
|`Symbol.toPrimitive`|此方法将对象转换为相应的基元值。 它由 `ToPrimitive` 抽象运算符在内部使用。|  
|`Symbol.toStringTag`|此属性返回一个字符串值，用于帮助创建对象的默认字符串说明。 它由内置方法 `Object.toString` 方法在内部使用。|  
|`Symbol.unscopables`|此属性返回一个对象，该对象的属性从关联对象的 `with` 环境绑定中排除。|  
  
## <a name="functions"></a>Functions  
 下表列出了 `Symbol` 对象的函数。  
  
|||  
|-|-|  
|属性|描述|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|返回指定密钥的符号，或者，如果密钥不存在，则使用新密钥创建新符号对象。|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|返回指定符号的密钥。|  
|||  
  
## <a name="example"></a>示例  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]