---
title: "为 JavaScript IntelliSense 创建 JSDoc 注释 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 为 JavaScript IntelliSense 创建 JSDoc 注释
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 中的 IntelliSense 显示你使用标准 JSDoc 注释添加到脚本中的信息。  你可以使用 JSDoc 注释来提供有关代码元素（如函数、字段和变量）的信息。  
  
## JSDoc 注释标记  
 intellisense 使用以下标准 JSDoc 注释标记显示有关代码的信息。  
  
|JSDoc 标记|语法|备注|  
|--------------|--------|--------|  
|@deprecated|@deprecated *说明*|指定一个不推荐使用的函数或方法。|  
|@description|@description *说明*|指定函数或方法的说明。|  
|@param|@param {*类型*} *参数名**说明*|指定函数或方法中的参数信息。<br /><br /> TypeScript 也支持 @paramTag。|  
|@property|@property {*类型*} *属性名称*|为在对象上定义的字段或成员指定信息（包括说明）。|  
|@returns|@returns {*类型*}|指定一个返回值。<br /><br /> 对于 TypeScript，请使用 @returnType（而非 @returns）。|  
|@summary|@summary *说明*|指定函数或方法的说明（与 @description 相同）。|  
|@type|@type {*类型*}|指定常量或变量的类型。|  
|@typedef|@typedef {*类型*} *自定义类型名称*|指定自定义的类型。|  
  
### 示例  
 以下示例演示了 `getArea` 函数的 @description、@param 和 @return JSDoc 标记的使用。  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 在前面的示例中，当你为 `getArea` 键入左括号时，IntelliSense 显示说明、参数和返回信息。  
  
 ![函数的 Intellisense 信息](~/docs/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 以下示例演示如何使用带 @property 标记的 @typedef 标记。  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 以下示例演示 @type JSDoc 标记的使用。  正如在此示例中所示，跟随在初始星号对 \(\*\*\) 之后的单个星号 \(\*\) 不是必需的。  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 以下示例演示如何使用 @deprecated JSDoc 标记。  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```