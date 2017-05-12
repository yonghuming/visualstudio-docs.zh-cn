---
title: "变量作用域 (JavaScript) | Microsoft Docs"
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
  - "作用域，JavaScript"
  - "变量作用域 [JavaScript]"
  - "变量，作用域 [JavaScript]"
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# 变量作用域 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 有两个范围：全局和局部。  在函数定义之外声明的变量是全局变量，它的值可在整个程序中访问和修改。  在函数定义内声明的变量是局部变量。  每当执行函数时，都会创建和销毁该变量，且无法通过函数之外的任何代码访问该变量。  JavaScript 不支持块范围（通过一组大括号 `{. . .}` 定义新范围），但块范围变量的特殊情况除外。  
  
## JavaScript 中的范围  
 虽然局部变量可具有与全局变量相同的名称，但它是完全独立的；更改一个变量的值不会影响另一个变量。  在声明局部变量的函数中，仅局部版本具有意义。  
  
```javascript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 在 JavaScript 中，变量就像它们在所在范围的开始被声明一样来计算。  有时，这会导致意外行为，如此处所示。  
  
```javascript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 当 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 执行一个函数时，它首先会查找所有变量声明，例如 `var someVariable;`。  它使用初始值 `undefined` 创建变量。  如果使用一个值声明变量（例如 `var someVariable = "something";`），则该变量的初始值仍为 `undefined`，并且仅当执行包含声明的行时才采用已声明的值。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 会在执行任何代码之前处理所有变量声明，无论是在条件块中声明还是在其他构造中声明。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 一旦找到所有变量，就会执行函数中的代码。  如果在函数内部隐式声明变量（即，该变量出现在赋值表达式的左侧但尚未使用 `var` 进行声明），则它将创建为全局变量。  
  
 在 JavaScript 中，内部（嵌套）函数将存储对局部变量的引用（即使在函数返回之后），这些局部变量存在于与函数本身相同的范围中。  这一组引用称为闭包。  在以下示例中，对内部函数的第二次调用所输出的消息与第一次调用相同（“Hello Bill”），因为外部函数的输入参数 `name` 是存储在内部函数闭包中的局部变量。  
  
```javascript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## 块范围变量  
 Internet Explorer 11 引入了对 [let](../../javascript/reference/let-statement-javascript.md) 和 [const](../../javascript/reference/const-statement-javascript.md) 这两个块范围变量的支持。  对于这些变量，大括号 `{. . .}` 定义新范围。  将其中一个变量设置为特定值时，该值仅适用于其设置所在的范围。  
  
 以下示例说明如何使用 `let` 和块范围。  
  
> [!NOTE]
>  以下代码在 Internet Explorer 11 标准模式及更高版本中受支持。  
  
```javascript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```