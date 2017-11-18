---
title: "decodeURI 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuri-function-javascript"></a>decodeURI 函数 (JavaScript)
获取未编码的版本的编码的统一资源标识符 (URI)。  
  
## <a name="syntax"></a>语法  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>备注  
 所需`URIstring`自变量是一个值，表示已编码的 URI。  
  
 使用`decodeURI`函数而不是不推荐使用`unescape`函数。  
  
 `decodeURI`函数返回一个字符串值。  
  
 如果`URIString`无效，URIError 时发生。  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>示例  
 下面的代码首先对 URI 组件进行编码，然后对它进行解码。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)   
 [Global 对象](../../javascript/reference/global-object-javascript.md)