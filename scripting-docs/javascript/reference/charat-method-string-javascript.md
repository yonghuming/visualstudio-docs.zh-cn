---
title: "charAt 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="charat-method-string-javascript"></a>charAt 方法 (String) (JavaScript)
返回指定索引处的字符。  
  
## <a name="syntax"></a>语法  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>参数  
 `strObj`  
 必需。 任何`String`对象或字符串文本。  
  
 `index`  
 必需。 所需的字符的从零开始索引。  
  
## <a name="remarks"></a>备注  
 `charAt`方法将返回字符值等于在指定的字符`index`。 字符串中的第一个字符位于索引 0 处，第二个位于索引 1，依此类推。 值的`index`都超出范围返回空字符串。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`charAt`方法：  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [String 对象](../../javascript/reference/string-object-javascript.md)