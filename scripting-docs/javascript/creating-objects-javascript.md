---
title: "Creating 对象 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="creating-objects-javascript"></a>Creating 对象 (JavaScript)
可通过多种方法在 JavaScript 中创建你自己的对象。 可以直接实例化 [Object 对象](../javascript/reference/object-object-javascript.md)，然后添加自己的属性和方法。 或者可以使用对象文字表示法来定义你的对象。 还可使用构造函数来定义对象。 有关使用构造函数的详细信息，请参阅[使用构造函数来定义类型](../javascript/advanced/using-constructors-to-define-types.md)。  
  
## <a name="example"></a>示例  
 下面的代码演示如何实例化对象和添加一些属性。 在此情况下，只有 `pasta` 对象具有 `grain`、`width` 和 `shape` 属性。  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>对象文字  
 只想创建一个对象实例时，还可以使用对象文字表示法。 下面的代码演示如何通过使用对象文字表示法来实例化对象。  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 还可以使用构造函数内的对象文字。  
  
> [!CAUTION]
>  下面描述的功能仅在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中受支持。  
  
 在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中，可以使用速记语法来创建对象文本。  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 以下示例演示如何使用速记语法来定义对象文字中的方法。  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 还可以在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 的对象文本中动态设置属性名称。 下面的代码示例使用 set 语法以动态方式创建对象的属性名称。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 下面的代码示例使用 get 语法以动态方式创建对象的属性名称。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 下面的代码示例通过使用[箭头函数语法](../javascript/functions-javascript.md)将 42 追加到属性名称来创建计算属性。  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```
