---
title: "toLowerCase 方法 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLowerCase method
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7510e074c11cf3d3f63b965bcd6f14946dc5a16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolowercase-method-javascript"></a>toLowerCase 方法 (JavaScript)
将字符串中的所有字母字符转换为小写。  
  
## <a name="syntax"></a>语法  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## <a name="remarks"></a>备注  
 `toLowerCase`方法具有对非字母字符没有影响。  
  
 下面的示例演示的效果`toLowerCase`方法：  
  
```JavaScript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleLowerCase 方法 (String)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 (String)](../../javascript/reference/touppercase-method-string-javascript.md)