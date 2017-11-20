---
title: "lastIndex 属性 (RegExp) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndex
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: lastIndex property
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5e24fe14d335e1494b13518543f56025625de0b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="lastindex-property-regexp-javascript"></a>lastIndex 属性 (RegExp) (JavaScript)
返回被搜索的字符串中的下一个匹配项的开始处的字符位置。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.lastIndex  
```  
  
## <a name="remarks"></a>备注  
 此属性与关联的对象始终是全局`RegExp`对象。  
  
 `lastIndex`属性是从零开始，即第一个字符的索引为零。 其初始值为-1。 无论何时执行成功匹配，将修改其值。  
  
 `lastIndex`通过修改属性`exec`和**测试**方法`RegExp`对象，与`match`，**替换**，和**拆分**方法`String`对象。  
  
 以下规则适用于值`lastIndex`:  
  
-   如果没有匹配项，`lastIndex`设置为-1。  
  
-   如果`lastIndex`大于字符串的长度**测试**和`exec`失败和`lastIndex`设置为-1。  
  
-   如果`lastIndex`等于字符串，如果模式将匹配空字符串的正则表达式匹配项的长度。 否则，匹配失败和`lastIndex`重置为-1。  
  
-   否则为`lastIndex`设置为最新的匹配之后的下一个位置。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`lastIndex`属性。 此函数循环访问搜索字符串，并输出**索引**和`lastIndex`每个单词在字符串中的值。  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**: [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)