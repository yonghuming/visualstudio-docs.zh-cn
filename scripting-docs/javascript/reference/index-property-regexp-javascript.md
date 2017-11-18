---
title: "index 属性 (RegExp) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: index
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Index property
- matching strings
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c6b11a5caf6e727b4d525b9a2d51eddd4542bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="index-property-regexp-javascript"></a>index 属性 (RegExp) (JavaScript)
返回被搜索的字符串中第一个成功匹配的开始位置的字符位置。 只读。  
  
## <a name="syntax"></a>语法  
  
```  
  
RegExp.index   
```  
  
## <a name="remarks"></a>备注  
 此属性与关联的对象始终是全局`RegExp`对象。  
  
 **索引**属性是从零开始。 初始值**索引**属性为-1。 每当将生成一个成功匹配，其值更改。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**索引**属性。 此函数循环访问搜索字符串，并输出**索引**和`lastIndex`每个单词在字符串中的值。  
  
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
      document.write (arr);  
      }  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**: [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)