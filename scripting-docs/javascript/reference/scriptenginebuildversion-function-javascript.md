---
title: "ScriptEngineBuildVersion 函数 (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion 函数"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ScriptEngineBuildVersion 函数 (JavaScript)
获取正在使用的脚本引擎的内部版本号。  
  
## 语法  
  
```  
ScriptEngineBuildVersion()  
```  
  
## 备注  
 返回值直接对应正在使用的脚本语言的动态链接库 \(DLL\) 中包含的版本信息。  
  
## 示例  
 下面的示例阐释了 `ScriptEngineBuildVersion` 函数的用法：  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## 要求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 请参阅  
 [ScriptEngine 函数](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion 函数](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion 函数](../../javascript/reference/scriptengineminorversion-function-javascript.md)