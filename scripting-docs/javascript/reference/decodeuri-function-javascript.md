---
title: "decodeURI 函数 (JavaScript) | Microsoft Docs"
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
  - "decodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "decodeURI 方法"
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# decodeURI 函数 (JavaScript)
获取一个已编码的统一资源标识符 \(URI\) 的非编码形式。  
  
## 语法  
  
```  
decodeURI(URIstring)  
```  
  
## 备注  
 必需的 `URIstring` 参数是表示已编码的 URI 的值。  
  
 请使用 `decodeURI` 函数而不要使用已弃用的 `unescape` 函数。  
  
 `decodeURI` 函数返回字符串值。  
  
 如果 `URIString` 无效，则将产生 URIError。  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 示例  
 下面的代码首先编码 URI 组件，然后对其进行解码。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global 对象](../../javascript/reference/global-object-javascript.md)