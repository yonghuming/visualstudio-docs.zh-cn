---
title: "const 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>const 语句 (JavaScript)
声明具有常数值的块范围变量。  
  
## <a name="syntax"></a>语法  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>参数  
 `constant1`  
 正在声明的变量的名称。  
  
 `value1`  
 分配给变量的初始值。  
  
## <a name="remarks"></a>备注  
 使用`const`语句可以声明具有常数值，其中的作用域仅限于块变量，在其中声明。 无法更改变量的值。  
  
 使用声明的变量`const`必须声明它时初始化。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `const` 语句的用法。  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [let 语句](../../javascript/reference/let-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)