---
title: "break 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>break 语句 (JavaScript)
终止当前循环或如果结合`label`，终止关联的语句。  
  
## <a name="syntax"></a>语法  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>备注  
 可选`label`参数指定从重大的语句的标签。  
  
 通常使用`break`中的语句`switch`语句并在`while`， `for`， `for...in`，或`do...while`循环。 您最常使用`label`中的参数`switch`语句，但它可在任何语句，无论是简单还是复合。  
  
 执行`break`语句从当前循环或语句，退出，并使用紧跟语句开始执行脚本。  
  
## <a name="examples"></a>示例  
 在此示例中，计数器是设置为从 1 到 99; 计数但是，`break`语句后 14 计数终止循环。  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 在下面的代码中，`break`语句是指`for`前面是循环`Inner:`语句。 当`j`等于 24 个，`break`语句将导致程序流退出该循环。 在每个行上打印数字 21 到 23。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [为..语句中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [标记的语句](../../javascript/reference/labeled-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)