---
title: "length 属性 (Function) (JavaScript) | Microsoft Docs"
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
  - "Length 属性"
  - "length 属性（函数）"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length 属性 (Function) (JavaScript)
获取为一个函数定义的参数数目。  
  
## 语法  
  
```  
  
functionName.length  
```  
  
## 备注  
 必要的 *functionName* 是该函数的名称。  
  
 创建函数的实例后，脚本引擎将该函数的 **length** 属性初始化为该函数定义中的参数数量。  
  
 调用函数时，如果其参数数量与其 **length** 属性的值不同，则发生的情况取决于该函数。  
  
## 示例  
 下面的示例阐释了 **length** 属性的用法：  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 请参阅  
 [arguments 属性（函数）](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 属性（数组）](../../javascript/reference/length-property-array-javascript.md)   
 [length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)