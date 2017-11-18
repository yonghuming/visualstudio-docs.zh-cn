---
title: "encodeURIComponent 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent 函数 (JavaScript)
将文本字符串编码为一个有效的组件的统一资源标识符 (URI)。  
  
## <a name="syntax"></a>语法  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>备注  
 所需`encodedURIString`参数是表示编码的 URI 组件的值。  
  
 `encodeURIComponent`函数将返回已编码的 URI。 如果通过将结果发送到`decodeURIComponent`，则返回原始字符串。 因为`encodeURIComponent`函数将所有字符都编码，请注意，如果该字符串表示路径如**/folder1/folder2/default.html**。 斜杠字符进行编码，并且无法有效如果作为请求发送到 web 服务器。 使用`encodeURI`如果字符串包含多个单个 URI 组件正常工作。  
  
## <a name="example"></a>示例  
 下面的代码首先对 URI 组件进行编码，然后对它进行解码。  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)