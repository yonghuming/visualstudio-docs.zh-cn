---
title: "decodeURIComponent 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent 函数 (JavaScript)
获取一个已编码的组件的统一资源标识符 (URI) 的未编码的版本。  
  
## <a name="syntax"></a>语法  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>备注  
 所需`encodedURIString`参数是表示编码的 URI 组件的值。  
  
 URIComponent 是一个完整的 URI 的一部分。  
  
 如果`encodedURIString`无效，URIError 时发生。  
  
## <a name="example"></a>示例  
 下面的代码首先进行编码，然后对 URI 进行解码。  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)