---
title: "正则表达式对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>正则表达式对象 (JavaScript)
一个对象，该对象包含正则表达式模式以及标识如何应用该模式的标志。  
  
## <a name="syntax"></a>语法  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>语法  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>参数  
 *重新*  
 必需。 正则表达式模式分配到的变量名称。  
  
 *模式*  
 必需。 要使用的正则表达式模式。 如果使用语法 1，则用“/”字符分隔模式。 如果使用语法 2，则将模式用引号引起来。  
  
 `flags`  
 可选。 如果使用语法 2，则将标志用引号引起来。 可以组合的可用标志包括：  
  
-   g (全局搜索出现的所有*模式*)  
  
-   i（忽略大小写）  
  
-   m（多行搜索）  
  
-   u (unicode)，启用 EcmaScript 6 [Unicode 功能](../../javascript/advanced/special-characters-javascript.md)。 仅在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中受支持。  
  
-   y（粘滞匹配），在正则表达式的 `lastIndex` 属性处搜索匹配项（而不是在后面的索引处搜索）。 在 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 中受支持。  
  
## <a name="remarks"></a>备注  
 **正则表达式**对象不应与全局混淆`RegExp`对象。 即使它们看起来相同，但它们彼此独立，截然不同。 属性**正则表达式**对象包含有关一个特定的唯一信息**正则表达式**实例时的全局属性`RegExp`对象包含出现时，不断更新有关每个匹配项的信息。  
  
 **正则表达式**对象存储用于搜索字符串的字符组合的模式。 后**正则表达式**创建对象，或者将其传递到字符串方法，或传递给正则表达式方法之一的字符串。 关于最近执行的搜索信息存储在全局 `RegExp` 对象中。  
  
 当预先知晓搜索字符串时，使用语法 1. 当搜索字符串频繁更改或未知时（例如，来自用户输入的字符串），使用语法 2.  
  
 *模式*参数将编译为内部格式在使用之前。 对于语法 1，*模式*加载脚本时编译。 对于语法 2，*模式*恰好在使用之前编译时，或者当**编译**调用方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**正则表达式**通过创建的对象 (re) 包含带其关联标志的正则表达式模式的对象。 在此情况下，生成**正则表达式**然后使用对象`match`方法：  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>示例  
 下面的示例更新了正则表达式模式以便搜索多个实例。  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>示例  
 使用 /y 标志时，如果匹配成功，则该标志会将 `lastindex` 更新为最后一个匹配项后的下一个字符的索引。 如果匹配失败，则该标志会将 `lastindex` 重置为 0。  
  
 下面的示例使用 /y 标志和`lastIndex` 属性在特定索引处搜索匹配项。  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>属性  
 [全局属性](../../javascript/reference/global-property-regular-expression-javascript.md)&#124;[ignoreCase 属性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)&#124;[multiline 属性](../../javascript/reference/multiline-property-regular-expression-javascript.md)&#124;[source 属性](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>方法  
 [compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md)&#124;[exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md)&#124;[测试方法](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u 标志在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中受支持。  
  
 y 标志在 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] 中受支持。  
  
## <a name="see-also"></a>另请参阅  
 [RegExp 对象](../../javascript/reference/regexp-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 对象](../../javascript/reference/string-object-javascript.md)