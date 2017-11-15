---
title: "数据属性和访问器属性 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="data-properties-and-accessor-properties"></a>数据属性和访问器属性
本部分包含你可能需要的关于数据属性和访问器属性的所有信息。  
  
### <a name="data-properties"></a>数据属性  
 数据属性是可以获取和设置值的属性。 数据属性将 `value` 和 `writable` 属性包含在其描述符中。  
  
 下表列出数据属性描述符的特性。  
  
|数据描述符特性|描述|默认|  
|-------------------------------|-----------------|-------------|  
|`value`|属性的当前值。|`undefined`|  
|`writable`|`true` 或 `false`。 如果将 `writable` 设置为 `true`，则可以修改属性值。|`false`|  
|`enumerable`|`true` 或 `false`。 如果将 `enumerable` 设置为 `true`，则属性可由 `for...in` 语句枚举。|`false`|  
|`configurable`|`true` 或 `false`。 如果将 `configurable` 设置为 `true`，则可以更改属性特性，并可以删除该属性。|`false`|  
  
 如果描述符没有 `value`、`writable`、`get` 或 `set` 特性，并且指定的属性名不存在，则会添加数据属性。  
  
 当 `configurable` 特性为 `false` 且 `writable` 为 `true` 时，在可以更改 `value` 和 `writable` 特性。  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>无需使用 defineProperty 即可添加数据属性  
 如果不通过使用 `Object.defineProperty``Object.defineProperties` 或 `Object.create` 函数添加数据属性，则 `writable`、`enumerable` 和 `configurable` 特性都将设置为 `true`。 添加该属性后，可以通过使用 `Object.defineProperty` 函数修改它。  
  
 可以使用以下方法添加数据属性：  
  
-   赋值运算符 (=)，如 `obj.color = "white";` 中所示  
  
-   对象文字，如 `obj = { color: "white", height: 5 };` 中所示  
  
-   构造函数，如[使用构造函数定义类型](../../javascript/advanced/using-constructors-to-define-types.md)中所述  
  
### <a name="accessor-properties"></a>访问器属性  
 每次设置或检索属性值时，访问器属性都会调用用户提供的函数。 访问器属性的描述符包含 `get` 特性和/或 `set` 特性。  
  
 下表列出了访问器属性描述符的特性。  
  
|访问器描述符特性|描述|默认|  
|-----------------------------------|-----------------|-------------|  
|`get`|返回属性值的函数。 此函数没有任何参数。|`undefined`|  
|`set`|设置属性值的函数。 它具有一个包含要分配值的参数。|`undefined`|  
|`enumerable`|`true` 或 `false`。 如果将 `enumerable` 设置为 `true`，则属性可由 `for...in` 语句枚举。|`false`|  
|`configurable`|`true` 或 `false`。 如果将 `configurable` 设置为 `true`，则可以更改属性特性，并可以删除该属性。|`false`|  
  
 当 `get` 访问器未定义且已尝试访问此属性值时，返回值 `undefined`。 当 `set` 访问器未定义且已尝试向访问器属性分配一个值时，不会发生任何事件。  
  
### <a name="property-modifications"></a>属性修改  
 如果对象已经具有此指定名称的属性，则将修改属性特性。 修改属性时，描述符中未指定的特性保持不变。  
  
 如果现有属性的 `configurable` 特性为 `false`，则唯一允许的修改是将 `writable` 特性从 `true` 更改为 `false`。  
  
 可以将数据属性更改为访问器属性，反之亦然。 如果这样做，则描述符中未指定的 `configurable` 和 `enumerable` 特性将保留在此属性中。 描述符中未指定的其他特性将设置为其默认值。  
  
 可以通过多次调用 `Object.defineProperty` 函数来增量地定义可配置的访问器属性。 例如，调用一次 `Object.defineProperty` 仅可定义一个 `get` 访问器。 以后调用相同的属性名可能会定义一个 `set` 访问器。 然后该属性将同时具有 `get` 访问器和 `set` 访问器。  
  
 要获取适用于现有属性的描述符对象，可以使用 [Object.getOwnPropertyDescriptor 函数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
 可以使用 [Object.seal 函数](../../javascript/reference/object-seal-function-javascript.md)和 [Object.freeze 函数](../../javascript/reference/object-freeze-function-javascript.md)来阻止修改属性特性。