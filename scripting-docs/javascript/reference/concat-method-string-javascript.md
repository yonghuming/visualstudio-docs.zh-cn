---
title: "concat 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>concat 方法 (String) (JavaScript)
返回包含两个或多个字符串的串联的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>参数  
 `string1`  
 必需。 `String`对象或字符串文本到所有其他指定连接字符串。  
  
 `string2,. . ., stringN`  
 可选。 要追加到结尾的字符串`string1`。  
  
## <a name="remarks"></a>备注  
 结果`concat`方法等效于： `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`。 在源或结果字符串中的值的更改不会影响其他字符串中的值。 如果任何参数不是字符串，它们首先之前都被转换为字符串串联到`string1`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`concat`方法与字符串一起使用时：  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [加法运算符 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)