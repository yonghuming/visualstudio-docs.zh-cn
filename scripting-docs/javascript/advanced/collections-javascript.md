---
title: "集合 (JavaScript) | Microsoft Docs"
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# 集合 (JavaScript)
可以使用集合对象 [Map](../../javascript/reference/map-object-javascript.md)、[Set](../../javascript/reference/set-object-javascript.md) 和 [WeakMap](../../javascript/reference/weakmap-object-javascript.md) 存储值和对象。  通过这些对象，可以使用键或值而非索引来轻松添加和检索成员。  若要使用索引访问集合的成员，请使用 `Array` 对象。  有关详细信息，请参阅[使用数组](../../javascript/advanced/using-arrays-javascript.md)。  
  
> [!CAUTION]
>  Internet Explorer 11 之前的浏览器版本不支持 `Map`、`Set` 和 `WeakMap`。  有关版本支持的更多信息，请参见[版本信息](../../javascript/reference/javascript-version-information.md)。  
  
## 使用集合  
 `Map` 和 `WeakMap` 对象存储键\/值对，并使你能够通过使用键来添加、检索和移除成员。  键和值可以为任何类型。  `Set` 对象存储任何类型的值。  
  
 通过 `Map` 和 `Set` 对象，你能够使用 `forEach` 方法枚举集合成员，并使用 `size` 方法检查集合大小。  与此相反，`WeakMap` 对象不可枚举。  对于此集合，键引用为弱保存。  如果要通过垃圾回收器来确定应用是否必须在内存中保留集合的每个成员，请使用 `WeakMap`。  例如，对于缓存对象极大、你不希望在内存中不必要地保存对象的缓存方案，这会非常有用。  在某些方案中，可以使用此对象防止内存泄漏。  
  
 以下示例演示如何使用 `Map` 对象。  在此示例中，你使用 `get` 和 `forEach` 访问成员。  `forEach` 中的回调函数最多可包含三个参数，提供当前集合元素的值、当前元素的键和集合对象本身。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 使用 `WeakMap` 与使用 `Map` 类似，但只能使用 `get` 检索成员。  有关示例，请参见 [WeakMap](../../javascript/reference/weakmap-object-javascript.md) 对象。  
  
 以下示例演示如何使用 `Set` 对象。  在此示例中，回调函数包含一个参数，即当前集合元素的值。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 请参阅  
 [高级 JavaScript](../../javascript/advanced/advanced-javascript.md)