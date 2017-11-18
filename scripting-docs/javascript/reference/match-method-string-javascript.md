---
title: "match 方法 (String) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match 方法 (String) (JavaScript)
匹配正则表达式中，一个字符串，并返回包含该搜索的结果的数组。  
  
## <a name="syntax"></a>语法  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>参数  
 `stringObj`  
 必需。 `String`对象或字符串文本在其上执行搜索。  
  
 `rgExp`  
 必需。 一个包含正则表达式模式和适用标志的正则表达式对象。 这也可以是变量名或字符串文本，其中包含正则表达式模式和标志。  
  
## <a name="remarks"></a>备注  
 如果`match`方法未找到匹配项，它将返回`null`。 如果它找到的匹配项，`match`返回的全局属性和数组，`RegExp`对象已更新以反映匹配项的结果。  
  
 如果全局标志 (`g`) 未设置，元素零的数组包含整个匹配项，而通过元素 1  *n* 包含任何子匹配项。 此行为是相同的行为[exec 方法 （正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)时未设置全局标志。 如果全局标志设置，通过元素 0  *n* 包含发生的所有匹配项。  
  
 如果全局标志未设置，返回的数组`match`方法具有两个属性，`input`和`index`。 `input`属性包含整个搜索的字符串。 `index`属性包含在完整的搜索字符串匹配的子字符串的位置。  
  
 如果标志`i`，则搜索不区分大小写。  
  
## <a name="example"></a>示例  
 下面的示例演示 `match` 方法的用法。  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [exec 方法 （正则表达式）](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace 方法 (String)](../../javascript/reference/replace-method-string-javascript.md)   
 [search 方法 (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法 （正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正则表达式编程 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [替换和子表达式 (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [反向引用 (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)