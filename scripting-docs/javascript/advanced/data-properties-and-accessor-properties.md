---
title: "数据属性和访问器属性 | Microsoft Docs"
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# 数据属性和访问器属性
本节包括您可能需要的有关数据属性和访问器属性的所有信息。  
  
### 数据属性  
 *数据属性* 是可获取和设置值的属性。  数据属性将 `value` 和 `writable` 属性包含在其描述符中。  
  
 下表列出了数据属性描述符的特性。  
  
|数据描述符特性|说明|默认|  
|-------------|--------|--------|  
|`value`|属性的当前值。|`undefined`|  
|`writable`|`true` 或 `false`。  如果 `writable` 设置为 `true`，则可以修改属性值。|`false`|  
|`enumerable`|`true` 或 `false`。  如果 `enumerable` 设置为 `true`，则可以由 `for…in` 语句枚举属性。|`false`|  
|`configurable`|`true` 或 `false`。  如果 `configurable` 设置为 `true`，则可以更改属性的特性且可以删除属性。|`false`|  
  
 如果描述符没有 `value`、`writable`、`get` 或 `set` 特性且指定的属性名不存在，则会添加数据属性。  
  
 在 `configurable` 特性为 `false` 且 `writable` 为 `true` 时，可以更改 `value` 和 `writable` 特性。  
  
#### 在未使用 defineProperty 的情况下添加的数据属性  
 如果您在未使用 `Object.defineProperty`、`Object.defineProperties` 或 `Object.create` 函数的情况下添加数据属性，则 `writable`、`enumerable` 和 `configurable` 特性都将设置为 `true`。  在添加属性后，可以使用 `Object.defineProperty` 函数修改属性。  
  
 可以使用以下方式来添加数据属性：  
  
-   赋值运算符 \(\=\)，如下所示：`obj.color = "white";`  
  
-   对象文本，如下所示：`obj = { color: "white", height: 5 };`  
  
-   构造函数，如[使用构造函数定义类型](../../javascript/advanced/using-constructors-to-define-types.md)中所述  
  
### 访问器属性  
 只要设置或检索属性值，*访问器属性* 就会调用用户提供的函数。  访问器属性的描述符包含 `get` 特性和\/或 `set` 属性。  
  
 下表列出了访问器属性描述符的特性。  
  
|访问器描述符特性|说明|默认|  
|--------------|--------|--------|  
|`get`|返回属性值的函数。  此函数没有参数。|`undefined`|  
|`set`|设置属性值的函数。  它具有一个包含要分配的值的参数。|`undefined`|  
|`enumerable`|`true` 或 `false`。  如果 `enumerable` 设置为 `true`，则可以由 `for…in` 语句枚举属性。|`false`|  
|`configurable`|`true` 或 `false`。  如果 `configurable` 设置为 `true`，则可以更改属性的特性且可以删除属性。|`false`|  
  
 在未定义 `get` 访问器时，如果尝试访问属性值，则将返回 `undefined` 值。  在未定义 `set` 访问器时，如果尝试向访问器属性赋值，则什么也不会发生。  
  
### 属性修改  
 如果对象已包含一个带指定名称的属性，则会修改该属性的特性。  在修改属性时，描述符中未指定的特性保持不变。  
  
 如果现有属性的 `configurable` 特性为 `false`，则唯一允许的修改是将 `writable` 特性从 `true` 更改为 `false`。  
  
 可以将数据属性更改为访问器属性，反之亦然。  如果这样做，描述符中未指定的 `configurable` 和 `enumerable` 特性将保留在属性中。  描述符中未指定的其他特性将设置为其默认值。  
  
 可以通过多次调用 `Object.defineProperty` 函数以增量方式定义可配置的访问器属性。  例如，一次 `Object.defineProperty` 调用可能仅定义一个 `get` 访问器。  稍后调用同一属性名称可能会定义一个 `set` 访问器。  之后，该属性将同时具有 `get` 访问器和 `set` 访问器。  
  
 若要获取适用于现有属性的描述符对象，可以使用 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
 可以使用 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)和 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)来阻止修改属性的特性。