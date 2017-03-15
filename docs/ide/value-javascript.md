---
title: "&lt;value&gt; (JavaScript) | Microsoft Docs"
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
  - "<value> JavaScript XML tag"
  - "value JavaScript XML tag"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`get` 和 `set`函数的 ECMAScript 3 属性的特定文档信息。  
  
## 语法  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### 参数  
 `type`  
 可选。  属性的数据类型。  这类型是以下值之一：  
  
-   一个ECMAScript语言类型是在ECMAScript5规范，例如`Number` 和 `Object`。  
  
-   一个 DOM 对象，例如 `HTMLElement`、`Window`和 `Document`。  
  
-   JavaScript 构造函数。  
  
 `integer`  
 可选。  如果 `type` 是 `Number`，指定属性时候是整型的。  设置 `true` 来描述属性是整型，否则，设置 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `domElement`  
 可选。  此属性是否定的；`type` 属性优先于此属性。  此特性属性是否是文档的属性的 DOM 元素。  设置 `true` 来指定DOM属性元素，否则，设置 `false`。  如果 `type` 属性没被设置，并且 `domElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将文档属性作 `HTMLElement`。  
  
 `mayBeNull`  
 可选。  指定该文档的属性是否可以设置为 null。  设置 `true` 来描述属性是否可以被设置为 null，否则，设置 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementType`  
 可选。  如果`type` 是 `Array`，属性找到数组中的指定类型。  
  
 `elementInteger`  
 可选。  如果 `type` 是 `Array`，并且 `elementType` 是 `Number`，此属性的指定该数组的元素是否是整数。  设置为 `true` 表明数组中的元素是整数，否则，将设置为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `elementDomElement`  
 可选。  此属性是否定的；`elementType` 属性优先于此属性。  如果 `type` 是 `Array`，此属性指定该数组的元素是否是 DOM 元素。  设置为 `true` 指定元素是 DOM 元素；否则，将设置为 `false`。  如果 `elementType` 属性没被设置，并且 `elementDomElement` 设置为 `true`，为执行时语句完成时，IntelliSense会将数组中的每个变量作为 `HTMLElement`。  
  
 `elementMayBeNull`  
 可选。  如果 `type` 是 `Array`，指定该数组的元素是否可以设置为 null。  设置为 `true` 它表明数组的元素可以设置为 null;否则，将设置为 `false`。  默认值为 `false`。  Visual Studio 不使用此属性提供 IntelliSense 信息。  
  
 `locid`  
 可选。  有关标识符属性的本地化信息。  该标识符是或成员 ID 或它对应于 OpenAjax 元数据在消息绑定的 `name` 属性值定义。  这个标示符依赖在 [\<loc\>](../ide/loc-javascript.md) 元素中的指定形式。  
  
 `description`  
 可选。  属性的说明。  
  
## 备注  
 ECMAScript 5属性，使用 [\<summary\>](../ide/summary-javascript.md) 元素。  
  
 在 `get` 或 `set` 函数前直接使用 `<value>` 元素。  
  
## 示例  
 下面的代码示例演示如何在 `get` 函数中使用 `<value>` 元素。  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## 请参阅  
 [XML 文档注释](../ide/xml-documentation-comments-javascript.md)