---
title: "substring 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring 方法 (String) (JavaScript)
返回在指定的位置的子字符串`String`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>参数  
 `start`  
 必需。 指示子字符串的开头从零开始的索引整数。  
  
 `end`  
 可选。 从零开始的索引整数，指示子字符串的末尾的位置。 子字符串中包含的字符最多，但不是包括，用表明字符`end`。  
  
 如果`end`省略，则从字符`start`返回通过原始字符串的末尾。  
  
## <a name="remarks"></a>备注  
 `substring`方法返回包含从子字符串的字符串`start`到，但不是包括`end`。  
  
 **子字符串**方法使用的较小值`start`和`end`作为起始点的子字符串。 例如，strvar.substring (0，3**)**和 strvar.substring （3，0） 返回相同的子字符串。  
  
 如果任一`start`或`end`是`NaN`或负数，它会替换零。  
  
 子字符串的长度等于绝对值的数值之间的差异的`start`和`end`。 例如，在 strvar.substring （0，3） 中返回子字符串的长度和 strvar.substring （3，0） 为 3。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**子字符串**方法。  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [substr 方法 (String)](../../javascript/reference/substr-method-string-javascript.md)