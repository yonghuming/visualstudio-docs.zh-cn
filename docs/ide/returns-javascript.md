---
title: "&lt;returns&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "returns JavaScript XML 标记"
  - "<returns> JavaScript XML 标记"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

函数或方法调用的指定文档信息。  
  
## 语法  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### 参数  
 `type`  
 可选。  数据类型的返回值。  这类型是以下值之一：  
  
-   一个ECMAScript语言类型是在ECMAScript5规范，例如`Number` 和 `Object`。  
  
-   一个 DOM 对象，例如 `HTMLElement`、`Window`和 `Document`。  
  
-   JavaScript 构造函数。  
  
 `integer`  
 可选。  如果 `type` 是 `Number`，指定返回值是否是整型的。  设置 `true` 来描述返回值是整型，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `domElement`  
 可选。  此属性是否定的；`type` 属性优先于此属性。  此指定属性是否是文档 DOM 的返回值元素。  设置 `true` 来指定DOM返回值元素，否则，设置 `false`。  如果 `type` 属性没被设置，并且 `domElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将文档返回值作 `HTMLElement`。  
  
 `mayBeNull`  
 可选。  指定文档返回值是否可以设置为 null。  设置 `true` 来描述返回值是否可以被设置为 null，否则，设置 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementType`  
 可选。  如果`type` 是 `Array`，属性找到数组中的指定类型。  
  
 `elementInteger`  
 可选。  如果 `type` 是 `Array`，并且 `elementType` 是 `Number`，此属性的指定该数组的元素是否是整数。  设置为 `true` 表明数组中的元素是整数，否则，将设置为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementDomElement`  
 可选。  此属性是否定的；`elementType` 属性优先于此属性。  如果 `type` 是 `Array`，此属性指定该数组的元素是否是 DOM 元素。  设置为 `true` 指定元素是 DOM 元素；否则，将设置为 `false`。  如果 `elementType` 属性没被设置，并且 `elementDomElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将数组中的每个变量作为 `HTMLElement`。  
  
 `elementMayBeNull`  
 可选。  如果 `type` 是 `Array`，指定该数组的元素是否可以设置为 null。  设置为 `true` 它表明数组的元素可以设置为 null;否则，将设置为 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `locid`  
 可选。  有关返回值的本地化信息的标识符。  该标识符是成员编号或它对应于OpenAjax元数据定义在消息绑定的 `name` 属性值。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 标签中的指定形式。  
  
 `value`  
 可选。  指定代码需要通过智能感知来评估而不是函数代码本身来评估。  例如，您可以使用这个属性来提供IntelliSense的异步回调，如 `Promise`。  使用 `value` 属性与 `<returns>` 元素可以绕过执行冗长的代码改进的IntelliSense的性能。  
  
 `description`  
 可选。  返回值的说明。  
  
## 备注  
 在任何声明之前，`<returns>` 元素必须在函数体中。  
  
## 示例  
 下面的代码示例演示如何使用 `<returns>` 元素。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)