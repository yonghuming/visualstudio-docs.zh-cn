---
title: "typeof 运算符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof 运算符 (JavaScript)
返回标识表达式数据类型的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>备注  
 *表达式*自变量是为哪种类型查找信息任何表达式。  
  
 `typeof`运算符将类型信息作为字符串返回。 有六个可能的值`typeof`返回:"数字，""string，""布尔，""对象，""函数"和"未定义"。  
  
 参数是可选的则括号`typeof`语法。  
  
## <a name="example"></a>示例  
 下面的示例测试变量的数据类型。  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>示例  
 下面的示例为数据类型的测试`undefined`声明和未声明的变量。  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Array.isArray 函数](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 函数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined 的常量](../../javascript/reference/undefined-constant-javascript.md)   
 [比较运算符](../../javascript/reference/comparison-operators-javascript.md)   
 [数据类型](../../javascript/data-types-javascript.md)   
 [运算符优先级](../../javascript/operator-subtractprecedence-javascript.md)   
 [运算符摘要 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)