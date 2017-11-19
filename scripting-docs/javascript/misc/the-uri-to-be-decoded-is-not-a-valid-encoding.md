---
title: "要解码的 URI 不有效编码 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>要解码的 URI 不是有效编码
你试图解码格式不正确的 URI （统一资源标识符）。 Uri 具有一个特殊的语法;大多数的非字母数字字符必须进行编码后，才可以在 URI 中使用。 你可以使用`encodeURI`和`encodeURIComponent`方法来创建 URI 从常规[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字符串。  
  
 一个完整的 URI 组成一系列组件和分隔符。 常规格式为：  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 在尖括号中的名称表示组件，与":"，"/"，";"和"？"是保留用作分隔符的字符。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   确保你尝试解码有效的 Uri。 你不能进行解码正常[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]字符串，因为它们可能包含无效字符。  
  
## <a name="see-also"></a>另请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)