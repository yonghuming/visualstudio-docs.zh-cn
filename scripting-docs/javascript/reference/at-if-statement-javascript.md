---
title: "@if语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@if语句 (JavaScript)
根据表达式的值有条件地执行一组语句。  
  
> [!WARNING]
>  Internet Explorer 11 标准模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用不支持条件编译。 Internet Explorer 10 标准模式和所有早期版本支持条件编译。  
  
## <a name="syntax"></a>语法  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>参数  
 *condition1、 condition2*  
 可选。 一个可强迫转换为布尔表达式的表达式。  
  
 `text1`  
 可选。 如果分析的文本`condition1`是**true**。  
  
 `text2`  
 可选。 如果分析的文本`condition1`是**false**和`condition2`是**true**。  
  
 `text3`  
 可选。 如果这两个分析的文本`condition1`和`condition2`是**false**。  
  
## <a name="remarks"></a>备注  
 在编写 `@if` 语句时，不必将每个子句放在独立的行中。 你可以使用多个 **@elif** 子句。 但是，所有 **@elif** 子句必须早于 **@else** 子句。  
  
 通常使用 `@if` 语句确定应使用若干选项中的哪个文本进行文本输出。  
  
 在为 ASP 或 ASP.NET 页或命令行程序编写的脚本中很少使用条件编译变量。 这是因为编译器的功能可以使用其他方法来确定。  
  
 当编写用于网页的脚本时，始终将条件编译代码添加到注释中。 这样，不支持条件编译的主机就可以将其忽略。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 **@if..。@elif..。@else...@end** 语句。  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>要求  
 在所有版本的 Internet Explorer 中受支持，但在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用中不受支持。  
  
## <a name="see-also"></a>另请参阅  
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on语句](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set 语句](../../javascript/reference/at-set-statement-javascript.md)