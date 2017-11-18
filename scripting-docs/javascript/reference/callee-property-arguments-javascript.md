---
title: "callee 属性 (arguments) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>callee 属性（自变量）(JavaScript)
返回`Function`正在执行的对象，即指定的正文文本`Function`对象。  
  
## <a name="syntax"></a>语法  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>备注  
 可选*函数*自变量是当前正在执行名称`Function`对象。  
  
 `callee`属性是成员的**参数**变得可用仅当关联的函数执行的对象。  
  
 初始值`callee`属性是`Function`对象正在执行。 这允许匿名函数是递归的。  
  
## <a name="example"></a>示例  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **适用于**: [arguments 对象](../../javascript/reference/arguments-object-javascript.md)&#124;[函数对象](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [caller 属性 (Function)](../../javascript/reference/caller-property-function-javascript.md)