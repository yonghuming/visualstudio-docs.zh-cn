---
title: "注释语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="comment-statements-javascript"></a>Comment 语句 (JavaScript)
使 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器忽略注释。  
  
## <a name="syntax"></a>语法  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>备注  
 `comment` 参数是你想包含在脚本中的任何注释的文本。 如果激活条件编译，则将使用 `condStatement` 参数。 如果使用单行注释，则“//”和“@”字符之间没有空格。  
  
 使用注释来防止 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 分析器读取脚本的各部分。 可使用注释将解释性备注包含在程序中。  
  
 如果使用单行注释，分析器将忽略注释标记和行尾间的任何文本。 如果使用单行注释，分析器将忽略开始标记和结束标记间的任何文本。  
  
 注释用于支持条件编译，同时与不支持此功能的浏览器保持兼容。 这些浏览器将这些形式的注释分别视为单行或多行注释。  
  
## <a name="example"></a>示例  
 下面的示例说明了注释的最常见的用法。  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用条件编译。 此示例使用特殊的注释分隔符，仅在 `@cc_on` 语句激活条件编译后使用这些分隔符。 不支持条件编译的脚本引擎仅看到表明条件编译不受支持的消息。  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]