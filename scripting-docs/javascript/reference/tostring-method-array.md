---
title: "toString 方法 (Array) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString 方法 (Array)
返回数组的字符串表示形式。  
  
## 语法  
  
```  
  
array.toString()  
```  
  
## 参数  
 `array`  
 必需。  要表示为字符串的数组。  
  
## 返回值  
 数组的字符串表示形式。  
  
## 备注  
 将 `Array` 的元素转换为字符串。  结果字符串被连接起来，用逗号分隔。  
  
## 示例  
 下面的示例阐释了如何将 **toString** 方法用于数组。  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]