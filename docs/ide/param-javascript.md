---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
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
  - "<param> JavaScript XML 标记"
  - "param JavaScript XML 标记"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在函数或方法中的指定参数的文档信息。  
  
## 语法  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### 参数  
 `name`  
 必需。  参数名。  
  
 `type`  
 可选。  参数的数据类型。  这类型是以下值之一：  
  
-   一个ECMAScript语言类型是在ECMAScript5规范，例如`Number` 和 `Object`。  
  
-   一个 DOM 对象，例如 `HTMLElement`、`Window`和 `Document`。  
  
-   JavaScript 构造函数。  
  
 `integer`  
 可选。  如果 `type` 是 `Number`，指定参数是否是整型的。  设置 `true` 来描述参数是整型，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `domElement`  
 可选。  此属性是否定的；`type` 属性优先于此属性。  此特性参数是否是文档的属性的 DOM 元素。  设置 `true` 来指定DO参数元素，否则，设置 `false`。  如果 `type` 属性没被设置，并且 `domElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将文档参数作 `HTMLElement`。  
  
 `mayBeNull`  
 可选。  指定该文档的参数是否可以设置为 null。  设置 `true` 来描述参数是否可以被设置为 null，否则，设置 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementType`  
 可选。  如果`type` 是 `Array`，属性找到数组中的指定类型。  
  
 `elementInteger`  
 可选。  如果 `type` 是 `Array`，并且 `elementType` 是 `Number`，此属性的指定该数组的元素是否是整数。  设置为 `true` 表明数组中的元素是整数，否则，将设置为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementDomElement`  
 可选。  此属性是否定的；`elementType` 属性优先于此属性。  如果 `type` 是 `Array`，此属性指定该数组的元素是否是 DOM 元素。  设置为 `true` 指定元素是 DOM 元素；否则，将设置为 `false`。  如果 `elementType` 属性没被设置，并且 `elementDomElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将数组中的每个变量作为 `HTMLElement`。  
  
 `elementMayBeNull`  
 可选。  如果 `type` 是 `Array`，指定该数组的元素是否可以设置为 null。  设置为 `true` 它表明数组的元素可以设置为 null;否则，将设置为 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `locid`  
 可选。  有关标识符参数的本地化信息。  该标识符是成员编号或它对应于OpenAjax元数据定义在消息绑定的 `name` 属性值。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 元素中的指定形式。  
  
 `parameterArray`  
 可选。  是否指定的文件参数可以在函数中重复调用，类似于 `String.format` 功能支持重复参数。  设置 `true` 来描述参数是否可以被设置重复，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `optional`  
 可选。  指定记录的参数是可选的调用函数。  设置 `true` 来描述参数是可选的，否则，设置 `false`。  
  
 `value`  
 可选。  指定代码需要通过智能感知来评估而不是函数代码本身来评估。  当参数类型是未定义时，您可以使用此属性提供类型信息。  例如，您可以使用 `value=’1’` 把参数类型作为数字。  
  
 `description`  
 可选。  参数的说明。  
  
## 备注  
 只有 `name` 特性是必需的。  所有其他特性都是可选的。  
  
 这个元素用于标注函数，例如 [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), 和 [\<returns\>](../ide/returns-javascript.md)，必须放在函数体内任何语句前面。  
  
 如果有多个 `<param>`元素具有相同的名称，`<param>` 中的一个元素被使用，而多余的元素将被忽略。  决定使用哪个元素的行为未定义。  如果 `name` 指的是不存在的参数，该元素将被忽略。  
  
## 示例  
 下面的代码示例演示如何使用 `<param>` 元素。  
  
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
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)