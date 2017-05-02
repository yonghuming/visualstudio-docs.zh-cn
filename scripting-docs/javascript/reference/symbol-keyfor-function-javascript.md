---
title: "Symbol.keyFor 函数 (JavaScript) | Microsoft Docs"
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
ms.assetid: f0b6f034-6d0a-421c-b1c6-52489411e9a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Symbol.keyFor 函数 (JavaScript)
返回指定符号的密钥。  
  
## 语法  
  
```vb  
Symbol.keyFor(sym);  
```  
  
#### 参数  
 `sym`  
 必需。  符号对象。  
  
## 备注  
 此方法搜索全局符号注册表中的符号。  
  
## 示例  
  
```javascript  
// Local symbol  
var sym1 = Symbol("desc");  
// Global symbol  
var sym2 = Symbol.for("desc");  
  
console.log(Symbol.keyFor(sym1)):  
console.log(Symbol.keyFor(sym2));  
  
// Output:  
// undefined  
// desc  
```  
  
## 要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]