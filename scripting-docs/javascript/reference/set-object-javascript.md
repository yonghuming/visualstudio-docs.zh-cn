---
title: "Set 对象 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set 对象 (JavaScript)
可以是任何类型的单个值的集合。  
  
## 语法  
  
```  
setObj = new Set()  
  
```  
  
## 备注  
 如果尝试将非唯一值添加到 `Set`，则新值不会添加到集合中。  
  
## 属性  
 下表列出了 `Set` 对象的属性。  
  
|Property|描述|  
|--------------|--------|  
|[构造函数](../../javascript/reference/constructor-property-set.md)|指定创建集的函数。|  
|[Prototype — 原型](../../javascript/reference/prototype-property-set.md)|为集返回对原型的引用。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|返回集中的元素数。|  
  
## 方法  
 下表列出了 `Set` 对象的方法。  
  
|方法|描述|  
|--------|--------|  
|[添加](../../javascript/reference/add-method-set-javascript.md)|添加元素至集。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|从集内移除所有元素。|  
|[删除](../../javascript/reference/delete-method-set-javascript.md)|从集中移除指定的元素。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|对集合中的每个元素执行指定操作。|  
|[有](../../javascript/reference/has-method-set-javascript.md)|如果集包含指定元素，则返回 `true`。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|返回集的字符串表示形式。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|返回指定对象的原始值。|  
  
## 示例  
 下面的示例演示如何将成员添加到一个设置，然后检索它们。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]