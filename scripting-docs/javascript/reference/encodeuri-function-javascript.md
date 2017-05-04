---
title: "encodeURI 函数 (JavaScript) | Microsoft Docs"
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
  - "encodeURI"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURI 方法"
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURI 函数 (JavaScript)
将文本字符串编码为有效的统一资源标识符 \(URI\)  
  
## 语法  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## 备注  
 必需的 `URIString` 参数是表示已编码的 URI 的值。  
  
 `encodeURI` 函数返回一个已编码的 URI。  如果将该结果传递给 `decodeURI`，则将返回原始字符串。  `encodeURI` 函数不对下列字符进行编码：“:”、“\/”、“;”和“?”。  请使用 `encodeURIComponent` 对这些字符进行编码。  
  
## 示例  
 以下代码会先对 URI 进行编码，然后对其进行解码。  
  
```javascript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)