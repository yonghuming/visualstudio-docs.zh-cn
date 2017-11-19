---
title: "unescape 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="unescape-function-javascript"></a>unescape 函数 (JavaScript)
将解码`String`使用编码对象`escape`函数。 已否决。  
  
## <a name="syntax"></a>语法  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>备注  
 所需`charString`自变量是`String`对象或要解码的文本。  
  
 `unescape`函数返回一个字符串值，包含的内容`charstring`。 所有与 %编码的字符*xx* ASCII 字符其等效的字符代替替换为十六进制格式。  
  
 中的字符编码**%u** *xxxx*格式 （Unicode 字符） 替换为具有十六进制编码的 Unicode 字符*xxxx*。  
  
> [!NOTE]
>  `unescape`函数不应该用于解码统一资源标识符 (URI)。 使用`decodeURI`和`decodeURIComponent`函数。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [decodeURI 函数](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 函数](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [escape 函数](../../javascript/reference/escape-function-javascript.md)   
 [String 对象](../../javascript/reference/string-object-javascript.md)