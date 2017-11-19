---
title: "length 属性 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>length 属性 (String) (JavaScript)
返回 `String` 对象的长度。  
  
> [!WARNING]
>  JavaScript 字符串是不可变，，因此不能修改字符串的长度。  
  
## <a name="syntax"></a>语法  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>备注  
 `length`属性包含一个整数，指示中的字符数`String`对象。 中的最后一个字符`String`对象的索引为我`length`-1。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`length`。 JavaScript 字符串是不可变，并且不能就地修改。 但是，你可以将发现反向的字符串写入到一个数组，然后调用`join`空的字符，由此产生任何分隔符字符的字符串。  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]