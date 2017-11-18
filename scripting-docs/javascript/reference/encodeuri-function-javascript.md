---
title: "encodeURI 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>encodeURI 函数 (JavaScript)
将文本字符串编码为有效的统一资源标识符 (URI)  
  
## <a name="syntax"></a>语法  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>备注  
 所需`URIString`自变量是一个值，表示已编码的 URI。  
  
 `encodeURI`函数将返回已编码的 URI。 如果通过将结果发送到`decodeURI`，则返回原始字符串。 `encodeURI`函数不会编码以下字符:":"，"/"，";"和"？"。 使用`encodeURIComponent`这些字符进行编码。  
  
## <a name="example"></a>示例  
 下面的代码首先进行编码，然后对 URI 进行解码。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)