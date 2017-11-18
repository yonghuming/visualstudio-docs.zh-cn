---
title: "caller 属性 （函数） (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller 属性（函数）(JavaScript)
获取调用当前函数的函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>备注  
 `functionName`对象的任何名称执行函数。  
  
 `caller`属性定义的函数仅在函数正在执行。 如果调用该函数从顶部的级别[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]程序，`caller`包含`null`。  
  
 如果`caller`字符串上下文中使用属性，则结果为相同`functionName`。`toString`，即会显示的函数的反编译的文本。  
  
 下面的示例演示 `caller` 属性的用法：  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [function 语句](../../javascript/reference/function-statement-javascript.md)