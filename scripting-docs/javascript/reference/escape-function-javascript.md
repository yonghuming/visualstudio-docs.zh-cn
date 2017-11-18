---
title: "escape 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape 函数 (JavaScript)
对字符串进行编码以便他们可以读取的所有计算机上。 已否决。  
  
## <a name="syntax"></a>语法  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>备注  
 所需`charString`自变量是下列任一`String`对象或文本进行编码。  
  
 **转义**函数将返回包含内容的字符串值 （以 Unicode 格式） `charstring`。 所有空格、 标点、 都重音符号以及任何其他非 ASCII 字符替换为`%` *xx*编码，其中*xx*等效于十六进制数字表示字符。 例如，空格返回为"%20"。  
  
 带值大于 255 存储使用的字符**%u** *xxxx*格式。  
  
> [!NOTE]
>  **转义**函数不应用于编码统一资源标识符 (URI)。 使用`encodeURI`和`encodeURIComponent`函数。  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [encodeURI 函数](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 函数](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [字符串对象](../../javascript/reference/string-object-javascript.md)   
 [unescape 函数](../../javascript/reference/unescape-function-javascript.md)