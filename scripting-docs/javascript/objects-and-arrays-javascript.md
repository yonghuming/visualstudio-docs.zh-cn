---
title: "对象和数组 (JavaScript) | Microsoft Docs"
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
  - "数组 [JavaScript]"
  - "组数 [JavaScript]，对象"
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 对象和数组 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 对象是属性和方法的集合。  方法是作为对象成员的函数。  属性是作为对象成员的一个值或一组值（以数组或对象的形式）。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 支持四种对象：  
  
-   内部对象（如 `Array` 和 `String`）。  
  
-   创建的对象。  
  
-   宿主对象（如 `window` 和 `document`）。  
  
-   ActiveX 对象。  
  
## Expando 属性和方法  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中的所有对象均支持 expando 属性和方法，这些属性和方法可在运行时动态添加和移除。  这些属性和方法可以有任何名称，并可用数字标识。  如果属性或方法的名称是简单的标识符，则可在对象名称与句点之后加入该属性，如以下代码中的 `myObj.name`、`myObj.age` 和 `myObj.getAge`：  
  
```javascript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 如果属性或方法的名称不是简单的标识符，或在编写脚本时不知道该属性，则可在方括号内使用表达式作为属性的索引。  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中所有 expando 属性的名称在添加到对象之前都被转换为字符串。  
  
```javascript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 有关从定义创建对象的信息，请参见[Creating 对象](../javascript/creating-objects-javascript.md)。  
  
## 作为对象的数组  
 在 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 中，对象和数组的处理方式几乎相同，因为数组仅是一类特殊的对象。  对象和数组都可以具有属性和方法。  
  
 数组具有 `length` 属性，而对象没有。  当你将值分配给索引大于其本身长度的数组的元素（例如 `myArray[100] = "hello"`）时，`length` 属性将自动增加到新的长度。  同样，如果使 `length` 属性变小，索引超过数组长度的所有元素将被删除。  
  
```javascript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 数组提供方法对成员进行循环访问和操作。  以下示例演示如何获得存储在数组中的对象的属性。  
  
```javascript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## 多维数组  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 不直接支持多维数组，但你可将多维数组存储在另一数组的元素中，从而获得多维数组的行为。（你可以在数组元素内部存储任何类型的数据，包括其他数组。）例如，以下代码为最大为 5 的数字生成一个乘法表。  
  
```javascript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```