---
title: "var 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>var 语句 (JavaScript)
声明变量。  
  
## <a name="syntax"></a>语法  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>参数  
 `variable1`  
 正在声明的变量的名称。  
  
 `value1`  
 分配给变量的初始值。  
  
## <a name="remarks"></a>备注  
 使用`var`语句来声明变量。 可以将值分配到的变量在声明它们或更高版本中你的脚本。  
  
 变量声明第一次它将显示在你的脚本。  
  
 你可以声明一个变量，而无需使用`var`关键字和分配到它的值。 这称为*隐式声明*，，不建议这样做。 隐式声明使变量全局作用域。 在声明在过程级别变量时，不过，你通常不希望其具有全局作用域。 若要避免使变量全局作用域，必须使用`var`在变量声明中的关键字。  
  
 如果你不初始化你的变量中`var`语句中，会自动分配[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]值`undefined`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`var`语句。  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [数组对象](../../javascript/reference/array-object-javascript.md)   
 [变量](../../javascript/variables-javascript.md)