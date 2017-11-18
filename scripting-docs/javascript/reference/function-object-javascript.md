---
title: "函数对象 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Function 对象 (JavaScript)
创建新的函数。  
  
## <a name="syntax"></a>语法  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>语法  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>参数  
 `functionName`  
 必需。 新创建的函数的名称  
  
 `argname1...argnameN`  
 可选。 该函数接受自变量列表。  
  
 `body`  
 可选。 一个字符串，包含的块[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]调用函数时要执行的代码。  
  
## <a name="remarks"></a>备注  
 该函数是中的基本数据类型[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。 语法 1 创建的函数值[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]将转换为`Function`对象在必要时。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]将转换`Function`函数中的值时创建语法 2 的对象时调用的函数。  
  
 语法 1 是创建新的函数中的标准方式[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。 语法 2 是用于显式创建函数对象的替代形式。  
  
 例如，若要声明将添加两个参数传递给它的函数时，可以执行在两种方式之一：  
  
## <a name="example-1"></a>示例 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>示例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 在任一情况下，你调用的代码线函数类似于以下：  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  当调用函数时，请确保你始终包括圆括号和任何必需的参数。 调用不带括号的函数会导致该函数本身才能返回，而不是函数的返回值。  
  
## <a name="properties"></a>属性  
 [0...n 属性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)&#124;[arguments 属性](../../javascript/reference/arguments-property-function-javascript.md)&#124;[callee 属性](../../javascript/reference/callee-property-arguments-javascript.md)&#124;[caller 属性](../../javascript/reference/caller-property-function-javascript.md)&#124;[构造函数属性](../../javascript/reference/constructor-property-object-javascript.md)&#124;[length 属性 （函数）](../../javascript/reference/length-property-function-javascript.md) &#124;[prototype 属性](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>方法  
 [apply 方法](../../javascript/reference/apply-method-function-javascript.md)&#124;[bind 方法](../../javascript/reference/bind-method-function-javascript.md)&#124;[调用方法](../../javascript/reference/call-method-function-javascript.md)&#124;[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)&#124;[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)   
 [new 运算符](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var 语句](../../javascript/reference/var-statement-javascript.md)