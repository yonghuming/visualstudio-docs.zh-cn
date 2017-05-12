---
title: "ScriptEngine 函数 (JavaScript) | Microsoft Docs"
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
  - "ScriptEngine"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngine 函数"
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ScriptEngine 函数 (JavaScript)
获取正在使用的脚本语言的名称。  
  
## 语法  
  
```  
ScriptEngine()  
```  
  
## 备注  
 `ScriptEngine` 函数返回“JScript”，它指示 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 是当前脚本引擎。  
  
## 示例  
 下面的示例阐释了 `ScriptEngine` 函数的用法：  
  
```javascript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 请参阅  
 [ScriptEngineBuildVersion 函数](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion 函数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函数](../../javascript/reference/scriptengineminorversion-function-javascript.md)