---
title: "valueOf 方法（数字） | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf 方法（数字）
返回指定数字的基元值。  
  
## 语法  
  
```  
  
number.valueOf()  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 返回该数字。  
  
## 备注  
 在下面的示例中，实例化的数字对象与此方法的返回值相同。  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## 要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]