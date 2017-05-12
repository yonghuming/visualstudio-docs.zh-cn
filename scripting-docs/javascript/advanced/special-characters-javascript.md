---
title: "特殊字符 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "反斜杠 (\)"
  - "转义序列"
  - "行终止符"
  - "Unicode 字符"
  - "空白字符"
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# 特殊字符 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 提供了可以包含在字符串中的转义序列，以创建不能直接键入的字符。  
  
## 备注  
 字符串值是一个由零或多个 Unicode 字符（字母、数字和其他字符）组成的序列。  字符串括在成对的单引号或双引号内。  括在单引号内的字符串可包含双引号。  括在双号内的字符串中可包含单引号。  
  
 字符串中的每个字符均可由一个转义序列表示。  转义序列以反斜杠 \(\\\) 开头，它通知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 解释器下一个字符是特殊字符。  
  
 可以使用 \\u*hhhh* 转义序列指定 Unicode 字符，其中 *hhhh* 是四位十六进制数。  Unicode 转义序列可以表示任何 16 位字符。  有关其他信息，请参阅 [Unicode 码位转义序列](#CodePoint)。  
  
 可对某些字符使用单字符转义序列。  例如，\\t 指定制表符。  
  
## 转义序列  
 下表列举了一些常用字符的转义序列。  
  
|Unicode 字符值|转义序列|含义|类别|  
|-----------------|----------|--------|--------|  
|\\u0008|\\b|Backspace||  
|\\u0009|\\t|制表符|空格|  
|\\u000A|\\n|换行|行结束符|  
|\\u000B|\\v<br /><br /> （参见此表后面的注释。）|垂直制表符|空格|  
|\\u000C|\\f|换页|空格|  
|\\u000D|\\r|回车|行结束符|  
|\\u0020||空格|空格|  
|\\u0022|\\"|双引号 \("\)||  
|\\u0027|\\'|单引号 \('\)||  
|\\u005C|\\\\|反斜杠 \(\\\)||  
|\\u00A0||不间断空格|空格|  
|\\u2028||行分隔符|行结束符|  
|\\u2029||段落分隔符|行结束符|  
|\\uFEFF||字节顺序标记|空格|  
  
 “类别”列指定字符是为空格还是行终止符。  [trim 方法 \(String\)](../../javascript/reference/trim-method-string-javascript.md)从字符串删除前导空格、尾随空格和行终止符。  
  
 反斜杠本身用作转义字符。  因此，无法直接将其键入脚本。  如果想写入反斜杠，则必须键入两个反斜杠 \(\\\\\)。  
  
> [!NOTE]
>  从 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 开始，无法通过测试垂直制表符 \(\\v\) 和“v”的等效性来将浏览器标识为 Internet Explorer。  在早期版本中，`"\v" === "v"` 表达式返回 `true`。  在 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 中，该表达式返回 `false`。  
  
## 示例  
  
### 说明  
 下面的示例阐释 \\\\ 和 \\' 转义序列。  
  
### 代码  
  
```javascript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## Unicode 码位转义序列  
 在 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] 中，完全支持 Unicode。  最常见的 Unicode 码位点由四个十六进制数表示，如 \/u0009 表示制表符。  Astral 码位（包括需要超过四个十六进制数的所有符号）现在支持采用简化格式。  通过使用“\\u{*码位*}”格式，可以以文本格式表示完整的 Unicode 字符集。  例如，要表示符号 "𠮷"，可以使用以下格式：“\\u{20BB7}”。  
  
 在下面的代码示例中，字符串都是等效的。  （\\uD842\\uDFB7 是以前的版本中用于指定此符号的解决方法。）  
  
```javascript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
  
```  
  
 RegExp 现在包括一个 \/u 标志，用于启用对 astral 码位的完整支持。  例如，在下面的代码示例中，正则表达式中的 \/u 标志允许匹配 astral 码位（句点匹配所提供的字符串中的任何字符）。  
  
```javascript  
"𠮷".match(/./u)[0].length == 2  
  
```  
  
 \/u 标志允许将新格式（\\u{码位}）分析为 Unicode 转义序列。  这是必需的，因为没有 \/u 标志的 \\u{xxxxx} 在正则表达式中具有不同的含义。  
  
> [!NOTE]
>  对于 astral 码位，长度始终为 2。  这与以前版本中的行为一致。  
  
 String 对象现在包含支持 astral 码位的两个新方法，即 String.codePointAt 和 String.fromCodePoint。  例如，可以使用 codePointAt 返回“𠮷”符号的等效码位。  
  
```javascript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 还可以使用 `for…of` 语句迭代码位。  
  
```javascript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## 请参阅  
 [String.fromCharCode 函数](../../javascript/reference/string-fromcharcode-function-javascript.md)