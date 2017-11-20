---
title: "class 语句 (JavaScript) |Microsoft 文档"
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="class-statement-javascript"></a>class 语句 (JavaScript)
声明新类。  
  
## <a name="syntax"></a>语法  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>参数  
 `classname`  
 必需。 类的名称。  
  
 `object`  
 可选。 新类从中继承属性和方法的对象或类。  
  
 `constructor`  
 可选。 初始化新类实例的构造函数。  
  
 `arg1...argN`  
 可选。 函数可理解的自变量的可选、以逗号分隔的列表。  
  
 `statements`  
 可选。 一个或多个 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 语句。  
  
 `static`  
 可选。 指定静态方法。  
  
 `method`  
 可选。 一个或多个可在类实例上调用的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 实例或静态方法。  
  
## <a name="remarks"></a>备注  
 借助类，你可以使用基于原型的继承、构造函数、实例方法和静态方法来创建新对象。 可使用类构造函数或类方法中的 `super` 对象来调用父类或父对象中的同一构造函数或方法。 或者，将 `extends` 附加到类名称后来指定新类从其继承方法的类或对象。  
  
## <a name="example"></a>示例  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>示例  
 还可以创建类的计算属性名称。 下面的代码示例使用 `set` 语法创建了一个计算属性名称。  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>示例  
 下面的代码示例使用 `get` 语法以动态方式创建了类的属性名称。  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]