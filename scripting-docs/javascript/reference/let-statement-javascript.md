---
title: "let 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>let 语句 (JavaScript)
声明块范围变量。  
  
## <a name="syntax"></a>语法  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>参数  
 `variable1`  
 正在声明的变量的名称。  
  
 `value1`  
 分配给变量的初始值。  
  
## <a name="remarks"></a>备注  
 使用`let`语句来声明的变量，其中的作用域仅限于块在其中声明。 可以将值分配到的变量在声明它们或更高版本中你的脚本。  
  
 使用声明的变量`let`不能使用其声明或错误会导致之前。  
  
 如果你不初始化你的变量中`let`语句中，会自动分配[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]值`undefined`。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `let` 语句的用法。  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [const 语句](../../javascript/reference/const-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)