---
title: "Creating 对象 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "构造函数"
  - "构造函数, 包括属性和方法"
  - "创建对象"
  - "创建对象, 关于创建对象"
  - "创建对象, 构造函数"
  - "创建对象, 原型"
  - "自定义对象"
  - "自定义对象, 创建"
  - "函数构造函数"
  - "初始化对象, 使用构造函数"
  - "对象, 创建 [JavaScript]"
  - "原型对象"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Creating 对象 (JavaScript)
可通过多种方法在 JavaScript 中创建你自己的对象。  可以直接实例化[Object 对象](../javascript/reference/object-object-javascript.md)，然后添加你自己的属性和方法。  或者可以使用对象文本表示法来定义你的对象。  还可使用构造函数来定义对象。  有关使用构造函数的详细信息，请参阅[使用构造函数定义类型](../javascript/advanced/using-constructors-to-define-types.md)。  
  
## 示例  
 下面的代码演示如何实例化对象和添加一些属性。  在此情况下，只有 `pasta` 对象具有 `grain`、`width` 和 `shape` 属性。  
  
```javascript  
var pasta = new Object();  
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
  
## 对象文本  
 只想创建一个对象实例时，还可以使用对象文本表示法。  下面的代码演示如何通过使用对象文本表示法来实例化对象。  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 还可以使用构造函数内的对象文本。  
  
> [!CAUTION]
>  下面描述的功能仅在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中受支持。  
  
 在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 中，可以使用速记语法来创建对象文本。  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 以下示例演示如何使用速记语法来定义对象文本中的方法。  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 还可以在 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] 的对象文本中动态设置属性名称。  下面的代码示例使用 set 语法以动态方式创建对象的属性名称。  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
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
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 下面的代码示例通过使用[箭头函数语法](../javascript/functions-javascript.md)将 42 追加到属性名称来创建计算属性。  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```