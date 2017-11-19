---
title: "undefined 常量 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>undefined 常量 (JavaScript)
一个值，永远不会定义，例如未初始化的变量。  
  
## <a name="syntax"></a>语法  
  
```  
undefined  
```  
  
## <a name="remarks"></a>备注  
 `undefined`常量为属于`Global`对象，并初始化脚本引擎时变得可用。 已声明了变量但未初始化，其值时，**未定义**。  
  
 如果尚未声明变量，不能比较到`undefined`，但你可以比较字符串"undefined"到变量的类型。  
  
 `undefined`常量时才能进行有用显式测试，或将变量设置为未定义。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`undefined`常量。  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>要求  
 `undefined`中引入了属性[!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]，并在只读方式进行[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]。  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [typeof 运算符](../../javascript/reference/typeof-operator-decrementjavascript.md)