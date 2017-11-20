---
title: "while 语句 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="while-statement-javascript"></a>while 语句 (JavaScript)
执行的语句或系列的语句，直到指定的条件为`false`。  
  
## <a name="syntax"></a>语法  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>参数  
 `expression`  
 必需。 循环每次迭代之前，会检查布尔表达式。 如果`expression`是`true`，循环执行。 如果`expression`是`false`，循环终止。  
  
 `statements`  
 可选。 如果要执行的一个或多个语句`expression`是`true`。  
  
## <a name="remarks"></a>备注  
 `while`语句检查`expression`第一次执行循环之前。 如果`expression`是`false`在此时，循环永远不会执行。  
  
## <a name="example"></a>示例  
 下面的示例阐释了 `while` 语句的用法。  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [continue 语句](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 语句](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 语句](../../javascript/reference/for-statement-javascript.md)   
 [for...in 语句](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)