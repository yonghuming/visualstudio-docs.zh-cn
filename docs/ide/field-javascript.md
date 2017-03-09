---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
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
  - "<field> JavaScript XML 标记"
  - "field JavaScript XML 标记"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定文档的信息，包括描述，要么是一个对象上定义一个字段或成员。  
  
## 语法  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### 参数  
 `name`  
 字段或成员的名称。  当 `<field>` 元素用于构造函数时，需要 `name` 并定义标记应用的成员。  当 `<field>` 元素直接注释一个字段时，此属性将被忽略，并且 Visual Studio 使用的名称是实际字段在源代码中的名称。  
  
 `static`  
 可选。  指定字段是否是构造函数的成员或构造函数所返回的对象的成员。  设置 `true` 将字段作为构造函数的成员。  设置 `false` 将字段作为构造函数的对象的成员返回。  
  
 `type`  
 可选。  字段的数据类型。  这类型是以下值之一：  
  
-   一个ECMAScript语言类型是在ECMAScript5规范，例如`Number` 和 `Object`。  
  
-   一个 DOM 对象，例如 `HTMLElement`、`Window`和 `Document`。  
  
-   JavaScript 构造函数。  
  
 `integer`  
 可选。  如果 `type` 是 `Number`，指定字段是否是整型的。  设置 `true` 来描述字段是整型，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `domElement`  
 可选。  此属性是否定的；`type` 属性优先于此属性。  此特性属性是否是文档的字段的 DOM 元素。  设置 `true` 来指定DOM字段元素，否则，设置 `false`。  如果 `type` 属性没被设置，并且 `domElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将文档字段作 `HTMLElement`。  
  
 `mayBeNull`  
 可选。  指定该文档的字段是否可以设置为 null。  设置 `true` 来描述字段是否可以被设置为 null，否则，设置 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementType`  
 可选。  如果`type` 是 `Array`，属性找到数组中的指定类型。  
  
 `elementInteger`  
 可选。  如果 `type` 是 `Array`，并且 `elementType` 是 `Number`，此属性的指定该数组的元素是否是整数。  设置为 `true` 表明数组中的元素是整数，否则，将设置为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementDomElement`  
 可选。  此属性是否定的；`elementType` 属性优先于此属性。  如果 `type` 是 `Array`，此属性指定该数组的元素是否是 DOM 元素。  设置为 `true` 指定元素是 DOM 元素；否则，将设置为 `false`。  如果 `elementType` 属性没被设置，并且 `elementDomElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将数组中的每个变量作为 `HTMLElement`。  
  
 `elementMayBeNull`  
 可选。  如果 `type` 是 `Array`，指定该数组的元素是否可以设置为 null。  设置为 `true` 它表明数组的元素可以设置为 null;否则，将设置为 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `helpKeyword`  
 可选。  F1帮助关键字。  
  
 `locid`  
 可选。  有关字段本地化信息的标识符。  该标识符是成员编号或它对应于OpenAjax元数据定义在消息绑定的 `name` 属性值。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 标签中的指定形式。  
  
 `value`  
 可选。  指定代码需要通过智能感知来评估而不是函数代码本身来评估。  对于 `<field>`，此属性支持构造函数，但是，不支持对象文本。  当参数类型是未定义时，您可以使用此字段提供类型信息。  例如，您可以使用 `value=’1’` 把字段类型作为数字。  
  
 `description`  
 可选。  关于字段的说明。  
  
## 备注  
 当你记录在一个构造函数中的字段，需要`name` 属性。  对于其他方案，`<field>` 元素的所有特性都是可选的。  
  
 当你记录一个构造函数时，`<field>` 元素必须在字段声明前出现。  `name` 特性必须与源代码的字段名称匹配。  对于对象成员，如果 `<field>` 元素在对象成员声明之前，`name` 属性可以省略。  
  
## 示例  
 下面的代码示例演示如何使用 `<field>` 元素。  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## 示例  
 下面的示例演示如何使用 `<field>` 元素和 `static` 特性来设置 `true`。  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## 示例  
 下面的示例演示如何使用 `<field>` 元素和 `static` 特性来设置 `false`。  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## 示例  
 下面的示例演示如何将 `<field>` 元素和 `value` 特性结合使用。  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)