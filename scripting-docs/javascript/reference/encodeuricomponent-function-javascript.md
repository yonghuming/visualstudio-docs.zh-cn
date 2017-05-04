---
title: "encodeURIComponent 函数 (JavaScript) | Microsoft Docs"
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
  - "encodeURIComponent"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "encodeURIComponent 方法"
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# encodeURIComponent 函数 (JavaScript)
将文本字符串编码为统一资源标识符 \(URI\) 的一个有效组件。  
  
## 语法  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## 备注  
 必需的 `encodedURIString` 参数是表示已编码的 URI 组件的值。  
  
 `encodeURIComponent` 函数返回一个已编码的 URI。  如果将该结果传递给 `decodeURIComponent`，则将返回原始字符串。  因为 `encodeURIComponent` 函数编码所有字符，所以请注意该字符串是否表示路径，例如 \/folder1\/folder2\/default.html。  斜杠字符将被编码，因此如果作为请求发送到 Web 服务器将无效。  如果字符串中包含多个 URI 组件，请使用 `encodeURI` 函数进行编码。  
  
## 示例  
 下面的代码首先编码 URI 组件，然后对其进行解码。  
  
```javascript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## 要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)