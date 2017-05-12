---
title: "Boolean 对象 (JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean 数据类型, Boolean 对象"
  - "Boolean 对象"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean 对象 (JavaScript)
创建新的布尔值。  
  
## 语法  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## 参数  
 `boolObj`  
 必需。  `Boolean` 对象分配到的变量名称。  
  
 `boolValue`  
 可选。  新对象的初始布尔值。  如果 `boolvalue` 被省略或者为 `false`、0、`null`、`NaN` 或空字符串，则 Boolean 对象的初始值为 `false`。  否则，初始值为 `true`。  
  
## 备注  
 `Boolean` 对象是布尔值数据类型的包装。  只要布尔值数据类型转换为 `Boolean` 对象，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就会隐式使用 `Boolean` 对象。  
  
 您很少显式实例化 `Boolean` 对象。  
  
## 属性  
 下表列出了 `Boolean` 对象的属性。  
  
|属性|说明|  
|--------|--------|  
|[constructor 属性](../../javascript/reference/constructor-property-boolean.md)|指定创建一个布尔值的函数。|  
|[prototype 属性](../../javascript/reference/prototype-property-boolean.md)|为 Boolean 返回对原型的引用。|  
  
<a name="js56jsobjarraymeth"></a>   
## 方法  
 下表列出了 `Boolean` 对象的方法。  
  
|方法|说明|  
|--------|--------|  
|[toString 方法](../../javascript/reference/tostring-method-boolean-1.md)|返回布尔值的字符串表示形式。|  
|[valueOf 方法](../../javascript/reference/valueof-method-boolean.md)|获取对布尔值的引用。|  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]