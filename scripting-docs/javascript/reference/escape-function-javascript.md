---
title: "escape 函数 (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "为字符串对象编码"
  - "Escape 方法"
  - "十六进制"
  - "字符串对象，编码"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape 函数 (JavaScript)
对字符串编码以便它们能在所有计算机上可读。  不推荐使用。  
  
## 语法  
  
```  
escape(charString)   
```  
  
## 备注  
 必需的 `charString` 参数是要编码的任何 `String` 对象或文本。  
  
 **escape** 函数返回一个包含 `charstring` 内容的字符串值（Unicode 格式）。  所有空格、标点、重音符号以及任何其他非 ASCII 字符都用 `%`*xx* 编码替换，其中 *xx* 等于表示该字符的十六进制数。  例如，空格返回为“%20”。  
  
 字符值大于 255 的字符以 **%u** *xxxx* 格式存储。  
  
> [!NOTE]
>  **escape** 函数不应用于编码“统一资源标识符”\(URI\)。  请改用 `encodeURI` 和 `encodeURIComponent` 函数。  
  
 **适用于**：[Global 对象](../../javascript/reference/global-object-javascript.md)  
  
## 要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 请参阅  
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函数](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)   
 [unescape 函数](../../javascript/reference/unescape-function-javascript.md)