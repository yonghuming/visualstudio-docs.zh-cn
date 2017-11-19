---
title: "switch 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="switch-statement-javascript"></a>switch 语句 (JavaScript)
当指定表达式的值与标签匹配时，允许执行一个或多个语句。  
  
## <a name="syntax"></a>语法  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>参数  
 `expression`  
 要计算的表达式。  
  
 `label`  
 使用标识符来匹配对`expression`。 如果`label`是`expression`，执行开头`statementlist`紧跟冒号，然后继续操作直到它遇到上述任何一`break`语句，它是可选的或结尾`switch`语句。  
  
 `statementlist`  
 要执行的一个或多个语句。  
  
## <a name="remarks"></a>备注  
 使用`default`子句，以提供无标签值匹配时要执行的语句`expression`。 它可以在任意位置出现`switch`代码块。  
  
 零个或多`label`可以指定块。 如果没有`label`匹配的值`expression`，和一个`default`用例未提供，不执行任何语句。  
  
 执行流经`switch`语句，如下所示：  
  
-   评估`expression`并查看`label`顺序，直到找到匹配项。  
  
-   如果`label`值等于`expression`，执行其伴随`statementlist`。  
  
     继续执行，直到`break`遇到语句，或`switch`语句结束。 这意味着多个`label`如果，则执行块`break`不使用语句。  
  
-   如果没有`label`等于`expression`，请转到`default`用例。 如果没有任何`default`种情况下，请转至最后一步。  
  
-   以下的末尾的语句处继续执行`switch`代码块。  
  
## <a name="example"></a>示例  
 下面的示例测试其类型的对象。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>示例  
 下面的代码的演示如果你未使用，会发生什么情况`break`语句。  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [if...else 语句](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)