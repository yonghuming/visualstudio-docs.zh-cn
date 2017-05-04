---
title: "this 语句 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "构造函数, 引用当前对象"
  - "this 语句"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this 语句 (JavaScript)
指当前的对象。  
  
## 语法  
  
```  
this.property  
```  
  
## 备注  
 必需的 `property` 参数是当前对象的属性之一。  
  
 `this` 关键字可在对象构造函数中用来引用当前对象。  
  
## 示例  
 在下面的示例中，**this** 引用新创建的 Car 对象，并为三个属性赋值：  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 如果在其他任何对象的范围之外使用，**this** 关键字通常引用 **window** 对象。  但是，在事件处理程序内，`this` 引用引发事件的 DOM 元素。  
  
 在以下代码（针对 Internet Explorer 9 和更高版本）中，事件处理程序输出具有“clicker”ID 的按钮的字符串版本。  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [使用 bind 方法](../../javascript/advanced/using-the-bind-method-javascript.md)