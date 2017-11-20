---
title: "for 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>for 语句 (JavaScript)
只要指定的条件为 true，则执行语句的块。  
  
## <a name="syntax"></a>语法  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>参数  
 `initialization`  
 可选。 一个表达式。 之前执行循环时，将只有一次执行此表达式。  
  
 `test`  
 可选。 布尔表达式。 如果`test`是`true`，`statement`执行。 如果`test`如果`false`，循环终止。  
  
 `increment`  
 可选。 一个表达式。 在每次通过循环的结尾处执行递增表达式。  
  
 `statement`  
 可选。 如果要执行的一个或多个语句`test`是**true**。 可以是复合语句。  
  
## <a name="remarks"></a>备注  
 您通常使用`for`循环时循环是要执行的已知的次数。 A`for`循环可用于循环访问数组和用于执行顺序处理。  
  
 条件表达式的测试会发生之前执行循环，因此`for`语句执行零次或多次。  
  
 中的任意行上`for`循环语句块中，你可以使用`break`语句退出循环，或者你可以使用`continue`语句将控制转移到循环的下一个迭代。  
  
## <a name="example"></a>示例  
 在下面的示例中，`for`语句执行括起来的语句，如下所示：  
  
-   首先，该变量的初始值`i`计算。  
  
-   然后，只要的值`i`小于或等于 9，`document.write`语句执行和`i`进行重新计算。  
  
-   当`i`大于 9，条件变为 false 和循环之外传输控制。  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>示例  
 所有的表达式`for`语句都是可选的。 在下面的示例中，`for`语句创建无限循环，和一个`break`语句用于退出循环。  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [为..语句中](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 语句](../../javascript/reference/while-statement-javascript.md)