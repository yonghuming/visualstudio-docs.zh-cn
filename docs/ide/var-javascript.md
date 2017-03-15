---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
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
  - "<var> JavaScript XML 标记"
  - "var JavaScript XML 标记"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

为变量指定文档信息。  
  
## 语法  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### 参数  
 `type`  
 可选。  变量的数据类型。  这类型是以下值之一：  
  
-   一个ECMAScript语言类型是在ECMAScript5规范，例如`Number` 和 `Object`。  
  
-   一个 DOM 对象，例如 `HTMLElement`、`Window`和 `Document`。  
  
-   JavaScript 构造函数。  
  
 `integer`  
 可选。  如果 `type` 是 `Number`，指定变量时候是整型的。  设置 `true` 来描述变量是整型，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `domElement`  
 可选。  此属性是否定的；`type` 属性优先于此属性。  此指定属性是否是文档 DOM 的变量元素。  设置 `true` 来 指定DOM变量元素，否则，设置 `false`。  如果 `type` 属性没被设置，并且 `domElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将文档变量作 `HTMLElement`。  
  
 `mayBeNull`  
 可选。  指定该文档的变量是否可以设置为 null。  设置 `true` 来描述变量是否可以被设置为 null，否则，设置 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementType`  
 可选。  如果`type` 是 `Array`，属性找到数组中的指定类型。  
  
 `elementInteger`  
 可选。  如果 `type` 是 `Array`，并且 `elementType` 是 `Number`，此属性的指定该数组的元素是否是整数。  设置为 `true` 表明数组中的元素是整数，否则，将设置为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementDomElement`  
 可选。  此属性是否定的；`elementType` 属性优先于此属性。  如果 `type` 是 `Array`，此属性指定该数组的元素是否是 DOM 元素。  设置为 `true` 指定元素是 DOM 元素；否则，将设置为 `false`。  如果 `elementType` 属性没被设置，并且 `elementDomElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将数组中的每个变量作为 `HTMLElement`。  
  
 `elementMayBeNull`  
 可选。  如果 `type` 是 `Array`，指定该数组的元素是否可以设置为 null。  设置为 `true` 它表明数组的元素可以设置为 null;否则，将设置为 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `helpKeyword`  
 可选。  F1的“帮助”关键字。  
  
 `locid`  
 可选。  有关标识符变量的本地化信息。  该标识符是成员编号或它对应于OpenAjax元数据定义在消息绑定的 `name` 属性值。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 标签中的指定形式。  
  
 `description`  
 可选。  有关变量对象的说明。  
  
## 示例  
 下面的代码示例演示如何使用 `<var>` 元素。  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)