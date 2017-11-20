---
title: "do...while 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while 语句 (JavaScript)
一次，执行一个语句块，然后重复执行循环，直到条件表达式的计算结果为`false`。  
  
## <a name="syntax"></a>语法  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>参数  
 `statement`  
 必需。 如果执行的语句`expression`是`true`。 可以是复合语句。  
  
 `expression`  
 必需。 可强制转换为布尔值的表达式`true`或`false`。 如果`expression`是`true`，再次执行循环。 如果`expression`是`false`，循环终止。  
  
## <a name="remarks"></a>备注  
 与不同`while`语句，`do...while`循环执行一次，然后再评估的条件表达式。  
  
 中的任意行上`do...while`块中，你可以使用`break`语句，以使程序流退出循环，或者你可以使用`continue`语句以直接转到`while`表达式。  
  
## <a name="example"></a>示例  
 在下面的示例中中的语句`do...while`循环继续只要变量执行`i`小于 10。  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>示例  
 在下面的示例中，即使不满足的条件，但一次执行循环内的语句。  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [为..语句中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)   
 [Labeled 语句](../../javascript/reference/labeled-statement-javascript.md)