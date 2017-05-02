---
title: "hasOwnProperty 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty 方法"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty 方法 (Object) (JavaScript)
确定某个对象是否具有带指定名称的属性。  
  
## 语法  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## 参数  
 `object`  
 必需。  对象的实例。  
  
 `proName`  
 必需。  一个属性名称的字符串值。  
  
## 备注  
 如果 `object` 具有带指定名称的属性，则 `hasOwnProperty` 方法返回 `true`，否则返回 `false`。  此方法不会检查对象原型链中的属性；该属性必须是对象本身的一个成员。  
  
 Internet Explorer 8 和低于其的版本的宿主对象不支持该属性。  
  
## 示例  
 在下面的示例中，所有 `String` 对象共享一个公共 split 方法。  下面的代码将显示 **false** 和 **true**。  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [in 运算符](../../javascript/reference/in-operator-decrementjavascript.md)