---
title: "length 属性 (Array) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array 对象"
  - "Length 属性"
  - "length 属性 (Array)"
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# length 属性 (Array) (JavaScript)
获取或设置数组的长度。  此数值比数组中所定义的最高位元素大 1。  
  
## 语法  
  
```  
  
numVar = arrayObj.length   
```  
  
## 参数  
 `numVar`  
 必需。  任意数值。  
  
 `arrayObj`  
 必需。  任意 `Array` 对象。  
  
## 备注  
 在 JavaScript 中，数组是稀疏的，且数组中的元素并不一定是连续的。  `length` 属性不一定是数组中的元素数。  例如，在下面的数组定义中，`my_array.length` 包含 7 而不包含 2：  
  
```javascript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 如果使 `length` 属性小于其它以前的值，则此数组将被截断，且数组索引大于或等于 `length` 属性新值的任何元素都将丢失。  
  
 如果使 length 属性大于其以前的值，则将展开数组，且创建的任何新元素都具有值 `undefined`。  
  
 下面的示例演示 `length` 属性的用法：  
  
```javascript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  从 Internet Explorer 9 标准模式开始，数组初始化中包含的尾随逗号的处理方式不同。