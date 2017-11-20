---
title: "slice 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice 方法 (String) (JavaScript)
返回字符串的片段。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>参数  
 `stringObj`  
 必需。 `String` 对象或字符串。  
  
 `start`  
 必需。 到的指定部分的开头的索引`stringObj`。  
  
 `end`  
 可选。 指定部分的末尾索引`stringObj`。 子字符串中包含的字符最多，但不是包括，用表明字符`end`。 如果未指定此值，子字符串将一直到末尾`stringObj`。  
  
## <a name="remarks"></a>备注  
 `slice`方法返回`String`对象，其中包含的指定的部分`stringObj`。  
  
 `slice`方法复制到，但不是包括的字符处所`end`。  
  
 如果`start`是负数，它将被视为*长度* +  `start`其中*长度*是字符串的长度。 如果`end`是负数，它将被视为*长度* + `end`。 如果`end`是省略，复制一直到末尾`stringObj`。 如果`end`之前发生`start`，任何字符被复制到新的字符串。  
  
## <a name="example"></a>示例  
 在第一个示例中，`slice`方法返回整个字符串。 在第二个示例中，`slice`方法返回的整个字符串，除最后一个字符。  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [slice 方法（数组）](../../javascript/reference/slice-method-array-javascript.md)