---
title: "WinRTError 对象 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "JavaScript, WinRTError 对象"
  - "WinRTError 对象 [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WinRTError 对象 (JavaScript)
当 Windows 运行时调用返回一个指示失败的 HRESULT 时，JavaScript 会将它转换为特殊的 Windows 运行时错误。  它仅在 Windows 运行时可用时，作为全局 JavaScript 命名空间的一部分，在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中提供。  
  
## 语法  
  
```  
  
errorObj = new WinRTError();   
```  
  
## 备注  
 WinRTError 错误类型仅可用于源自 Windows 运行时 API 的错误。  
  
## 示例  
 下面的示例演示了如何引发和捕获 WinRTError。  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## 方法  
 WinRTError 对象没有任何方法。  
  
## 属性  
 WinRTError 对象具有与 [Error 对象](../../javascript/reference/error-object-javascript.md) 对象相同的属性。  
  
## 要求  
 WinRTError 对象仅在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 应用中受支持，在 Internet Explorer 中不受支持。  
  
## 请参阅  
 [Error 对象](../../javascript/reference/error-object-javascript.md)