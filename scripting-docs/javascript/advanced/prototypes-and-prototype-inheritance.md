---
title: "原型和原型继承 | Microsoft Docs"
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
  - "原型 [JavaScript]"
  - "原型继承 [JavaScript]"
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 原型和原型继承
在 JavaScript 中，`prototype` 是函数的一个属性，同时也是由构造函数创建的对象的一个属性。  函数的原型为对象。  它主要在函数用作构造函数时使用。  
  
```javascript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 在上面的示例中，`Vehicle` 函数的原型是使用 `Vehicle` 构造函数实例化的任何对象的原型。  
  
## 使用原型添加属性和方法  
 可以使用 `prototype` 属性向对象添加属性和方法，甚至于已创建的对象也是如此：  
  
```javascript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 `testColor` 的值为“red”。  
  
 你甚至可以向预定义的对象添加属性和方法。  例如，你可以在 `String` 原型对象上定义一个 `Trim` 方法，脚本中的所有字符串都将继承该方法。  
  
```javascript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### 可使用原型通过 Object.create 从一个对象派生另一个对象  
 `prototype` 对象可用于从一个对象派生另一个对象。  例如，你可以使用 [Object.create](../../javascript/reference/object-create-function-javascript.md) 函数派生使用我们之前定义的 `Vehicle` 对象的原型（以及所需的任何新属性）的新对象 `Bicycle`。  
  
```javascript  
var Bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 `Bicycle` 对象具有属性 `wheels`、`engine`、`color` 和 `pedals`，并且其原型为 `Vehicle.prototype`。  JavaScript 引擎会查找 `Bicycle` 的 `pedals` 属性，并查看原型链以便查找 `Vehicle` 的 `wheels`、`engine` 和 `color`。  
  
### 更改对象的原型  
 在 Internet Explorer 11 中，可以通过 [\_\_proto](../../javascript/reference/proto-property-object-javascript.md) 属性用新原型替换对象或函数的内部原型。  使用此属性时，将继承新原型的属性和方法以及其原型链中的其他属性和方法。  
  
 以下示例演示如何更改对象的原型。  此示例演示当更改对象原型时，对象的继承属性将如何更改。  
  
```javascript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```