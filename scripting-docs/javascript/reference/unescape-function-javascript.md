---
title: "unescape 函数 (JavaScript) | Microsoft Docs"
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
  - "unescape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Unescape 方法"
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# unescape 函数 (JavaScript)
解码用 `escape` 函数进行编码的 `String` 对象。  不推荐使用。  
  
## 语法  
  
```  
unescape(charString)   
```  
  
## 备注  
 必需的 `charString` 参数是要解码的 `String` 对象或文本。  
  
 `unescape` 函数返回包含 `charstring` 的内容的字符串值。  所有以 %*xx* 十六进制形式编码的字符都用 ASCII 字符集当中等效的字符代替。  
  
 以 **%u** *xxxx* 格式（Unicode 字符）编码的字符用十六进制编码 *xxxx* 的 Unicode 字符代替。  
  
> [!NOTE]
>  `unescape` 函数不应用于解码“统一资源标识符”\(URI\)。  请改用 `decodeURI` 和 `decodeURIComponent` 函数。  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 函数](../../javascript/reference/escape-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)