---
title: "exec 方法 （正则表达式） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>exec 方法（正则表达式）(JavaScript)
使用正则表达式模式中，对字符串执行搜索并返回包含该搜索的结果的数组。  
  
## <a name="syntax"></a>语法  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>参数  
 `rgExp`  
 必需。 实例**正则表达式**包含正则表达式模式和适用标志的对象。  
  
 `str`  
 必需。 `String`对象或字符串文本在其上执行搜索。  
  
## <a name="remarks"></a>备注  
 如果`exec`方法未找到匹配项，它将返回`null`。 如果它找到的匹配项，`exec`返回的全局属性和数组，`RegExp`对象已更新以反映匹配项的结果。 数组的元素零包含整个匹配项，而元素 1-  *n* 包含匹配中发生任何子匹配项。 此行为是相同的行为的`match`方法，而全局标志 (**g**) 设置。  
  
 如果为正则表达式，设置了全局标志`exec`搜索的值指示的位置开始的字符串`lastIndex`。 如果未设置全局标志，`exec`将忽略的值`lastIndex`和从字符串的开头搜索。  
  
 返回的数组`exec`方法具有三个属性，**输入**，**索引**和**lastIndex。** **输入**属性包含整个搜索的字符串。 **索引**属性包含在完整的搜索字符串匹配的子字符串的位置。 `lastIndex`属性包含匹配项中的最后一个字符后面的位置。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`exec`方法：  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [match 方法 (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search 方法 (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法 （正则表达式）](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正则表达式编程 (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)