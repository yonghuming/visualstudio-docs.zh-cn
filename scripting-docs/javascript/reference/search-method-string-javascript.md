---
title: "search 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>search 方法 (String) (JavaScript)
在正则表达式搜索中查找第一个子字符串匹配项。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>参数  
 `stringObj`  
 必需。 `String`对象或字符串文本在其上执行搜索。  
  
 `rgExp`  
 必需。 实例**正则表达式**包含正则表达式模式和适用标志的对象。  
  
## <a name="return-value"></a>返回值  
 如果找到匹配项，则**搜索**方法返回一个整数值，该值指示从该字符串的开头的偏移量发生第一个匹配项的位置。 如果不找到任何匹配，则返回-1。  
  
## <a name="remarks"></a>备注  
 你还可以设置`i`导致执行搜索，不区分大小写的标志。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**搜索**方法。  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [exec 方法 （正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 (String)](../../javascript/reference/match-method-string-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace 方法 (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [test 方法 （正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正则表达式编程 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)