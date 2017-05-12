---
title: "decodeURIComponent 函数 (JavaScript) | Microsoft Docs"
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
  - "decodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURIComponent 方法"
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# decodeURIComponent 函数 (JavaScript)
获取统一资源标识符 \(URI\) 的一个已编码组件的非编码形式。  
  
## 语法  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## 备注  
 必需的 `encodedURIString` 参数是表示已编码的 URI 组件的值。  
  
 URIComponent 是完整 URI 的一部分。  
  
 如果 `encodedURIString` 无效，则将产生 URIError。  
  
## 示例  
 以下代码会先对 URI 进行编码，然后对其进行解码。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)