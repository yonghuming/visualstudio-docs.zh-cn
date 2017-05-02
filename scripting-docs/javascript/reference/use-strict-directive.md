---
title: "使用严格指令 | Microsoft Docs"
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
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "严格模式"
  - "使用严格指令"
  - "使用严格"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用严格指令
限制 JavaScript 中某些功能的使用。  仅在 Internet Explorer 10 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] app 中受支持。  
  
## 语法  
  
```javascript  
use strict  
```  
  
## 备注  
  
## 示例  
 由于在严格模式中，必须用 `var` 声明所有变量，因此下面的代码将导致语法错误。  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## 请参阅  
 [严格模式](../../javascript/advanced/strict-mode-javascript.md)