---
title: "字符串对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>String 对象 (JavaScript)
允许操作和格式化文本字符串以及确定和定位字符串中的子字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>参数  
 `newString`  
 必需。 `String` 对象分配到的变量名称。  
  
 `stringLiteral`  
 可选。 任何 Unicode 字符组。  
  
## <a name="remarks"></a>备注  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 提供了可以包含在字符串中的转义序列，以创建不能直接键入的字符。 例如，`\t` 指定制表符。 有关详细信息，请参阅[特殊字符](../../javascript/advanced/special-characters-javascript.md)。  
  
## <a name="string-literals"></a>字符串  
 A*字符串文本*用单引号或双引号括起来的零个或多个字符。 字符串文本具有 `string` 的主（基元）数据类型。 A*字符串对象*通过创建[new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)，且其数据类型为`Object`。  
  
 以下示例显示字符串文本的数据类型与 `String` 对象的数据类型不同。  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>用于字符串的方法  
 在对字符串调用一个方法时，字符串将临时转换为字符串包装器对象。 字符串将被视为好像是使用 `new` 运算符创建的。  
  
 以下示例将 `toUpperCase` 方法应用于字符串。  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>访问单个字符  
 你可以将字符串的单个字符作为只读数组索引属性访问。 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 中已引入此功能。 以下示例访问单个字符串字符。  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>要求  
 `String Object`中已引入 [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]。 更高版本中已引入以下列表中的某些成员。  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>属性  
 下表列出了 `String` 对象的属性。  
  
|属性|描述|  
|--------------|-----------------|  
|[constructor 属性](../../javascript/reference/constructor-property-string.md)|指定用于创建对象的函数。|  
|[length 属性（字符串）](../../javascript/reference/length-property-string-javascript.md)|返回 `String` 对象的长度。|  
|[prototype 属性](../../javascript/reference/prototype-property-string.md)|为对象的类返回原型的引用。|  
  
## <a name="functions"></a>函数  
 下表列出了 `String` 对象的函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[String.fromCharCode 函数](../../javascript/reference/string-fromcharcode-function-javascript.md)|从若干 Unicode 字符值中返回一个字符串。|  
|[String.fromCodePoint 函数](../../javascript/reference/string-fromcodepoint-function-javascript.md)|返回与 Unicode UTF-16 码位关联的字符串。|  
|[String.raw 函数](../../javascript/reference/string-raw-function-javascript.md)|返回模板字符串的原始字符串形式。|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>方法  
 下表列出了 `String` 对象的方法。  
  
|方法|描述|  
|------------|-----------------|  
|[anchor 方法](../../javascript/reference/html-tag-methods-javascript.md)|将具有 NAME 特性的 HTML 定位点放置在文本两侧。|  
|[big 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<大 > 标记放置在文本两侧。|  
|[blink 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<BLINK > 标记放置在文本两侧。|  
|[bold 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<B > 标记放置在文本两侧。|  
|[charAt 方法](../../javascript/reference/charat-method-string-javascript.md)|返回指定索引处的字符。|  
|[charCodeAt 方法](../../javascript/reference/charcodeat-method-string-javascript.md)|返回指定字符的 Unicode 编码。|  
|[codePointAt 方法](../../javascript/reference/codepointat-method-string-javascript.md)|返回一个 Unicode utf-16 字符的码位。|  
|[concat 方法（字符串）](../../javascript/reference/concat-method-string-javascript.md)|返回由提供的两个字符串串联而成的字符串。|  
|[endsWith 方法](../../javascript/reference/endswith-method-string-javascript.md)|返回一个布尔值，该值指示字符串或子字符串是否以传入字符串结尾。|  
|[includes 方法](../../javascript/reference/includes-method-string-javascript.md)|返回一个布尔值，该值指示传入字符串是否包含在字符串对象中。|  
|[fixed 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<TT > 标记放置在文本两侧。|  
|[fontcolor 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<字体 > 标记具有 COLOR 特性放置在文本两侧。|  
|[fontsize 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<字体 > 标记具有 SIZE 特性放置在文本两侧。|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否具有指定名称的属性。|  
|[indexOf 方法（字符串）](../../javascript/reference/indexof-method-string-javascript.md)|返回字符串内第一次出现子字符串的字符位置。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|返回一个布尔值，该值指示某个对象是否存在于另一个对象的原型链中。|  
|[italics 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<我 > 标记放置在文本两侧。|  
|[lastIndexOf 方法（字符串）](../../javascript/reference/lastindexof-method-string-javascript.md)|返回字符串内子字符串的最后一个匹配项。|  
|[link 方法](../../javascript/reference/html-tag-methods-javascript.md)|将具有 HREF 特性的 HTML 定位点放置在文本两侧。|  
|[localeCompare 方法](../../javascript/reference/localecompare-method-string-javascript.md)|返回一个值，该值指示两个字符串在当前区域设置中是否相等。|  
|[match 方法](../../javascript/reference/match-method-string-javascript.md)|通过使用提供的字符串中搜索**正则表达式**对象，并以数组形式返回结果。|  
|[normalize 方法](../../javascript/reference/normalize-method-string-javascript.md)|返回指定字符串的 Unicode 范式。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|返回一个布尔值，该值指示指定属性是否为对象的一部分且是否可枚举。|  
|[repeat 方法](../../javascript/reference/repeat-method-string-javascript.md)|返回一个新的字符串对象，它的值等于重复了指定次数的原始字符串。|  
|[replace 方法](../../javascript/reference/replace-method-string-javascript.md)|使用正则表达式替换字符串中的文本并返回结果。|  
|[search 方法](../../javascript/reference/search-method-string-javascript.md)|返回正则表达式搜索中第一个子字符串匹配项的位置。|  
|[slice 方法（字符串）](../../javascript/reference/slice-method-string-javascript.md)|返回字符串的片段。|  
|[small 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<小 > 标记放置在文本两侧。|  
|[split 方法](../../javascript/reference/split-method-string-javascript.md)|返回一个字符串拆分为若干子字符串时所产生的字符串数组。|  
|[startsWith 方法](../../javascript/reference/startswith-method-string-javascript.md)|返回一个布尔值，该值指示字符串或子字符串是否以传入字符串开头。|  
|[strike 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<STRIKE > 标记放置在文本两侧。|  
|[sub 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<子 > 标记放置在文本两侧。|  
|[substr 方法](../../javascript/reference/substr-method-string-javascript.md)|返回一个从指定位置开始且具有指定长度的子字符串。|  
|[substring 方法](../../javascript/reference/substring-method-string-javascript.md)|返回 `String` 对象中指定位置处的子字符串。|  
|[sup 方法](../../javascript/reference/html-tag-methods-javascript.md)|将 HTML 放置\<SUP > 标记放置在文本两侧。|  
|[toLocaleLowerCase 方法](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|返回一个字符串，其中所有字母字符都转换为小写形式，并将考虑主机环境的当前区域设置。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|返回使用当前区域设置转换为字符串的对象。|  
|[toLocaleUpperCase 方法](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|返回一个字符串，其中所有字母字符都转换为大写形式，并将考虑主机环境的当前区域设置。|  
|[toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)|返回一个字符串，其中所有字母字符都转换为小写形式。|  
|[toString 方法](../../javascript/reference/tostring-method-string-1.md)|返回字符串。|  
|[toUpperCase 方法](../../javascript/reference/touppercase-method-string-javascript.md)|返回一个字符串，其中所有字母字符都转换为大写形式。|  
|[trim 方法](../../javascript/reference/trim-method-string-javascript.md)|返回已移除前导空格、尾随空格和行终止符的字符串。|  
|[valueOf 方法](../../javascript/reference/valueof-method-string.md)|返回字符串。|  
  
## <a name="see-also"></a>另请参阅  
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [滚动、 平移和缩放示例应用](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)