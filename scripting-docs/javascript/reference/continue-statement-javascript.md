---
title: "continue 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="continue-statement-javascript"></a>continue 语句 (JavaScript)
停止循环的当前迭代，并启动新的迭代。  
  
## <a name="syntax"></a>语法  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>备注  
 可选`label`自变量指定到语句`continue`适用。  
  
 你可以使用`continue`语句仅内`while`， `do...while`，**为**，或`for...in`循环。 执行`continue`语句停止循环的当前迭代并继续循环的开头的程序流。 这具有对不同类型的循环的以下影响：  
  
-   `while`和`do...while`循环测试其条件，并将如果为 true，请再次执行循环。  
  
-   `for`循环执行其增量表达式，并将测试表达式是否为 true，请再次执行循环。  
  
-   `for...in`循环继续进行到指定的变量的下一个字段，并再次执行循环。  
  
## <a name="examples"></a>示例  
 在此示例中，循环访问从 1 到 9。 之间的语句`continue`和结束`for`正文将跳过，因为使用了`continue`以及表达式语句`(i < 5)`。  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 在下面的代码中，`continue`语句是指`for`前面是循环`Inner:`标签。 当`j`为 24，`continue`语句使`for`循环转到下一个迭代。 在每个行上打印数字 21 到 23 和 25 到 30。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [为..语句中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [标记的语句](../../javascript/reference/labeled-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)