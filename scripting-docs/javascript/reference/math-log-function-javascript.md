---
title: "Math.log 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: log
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- log method
- Math object
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62bfb6bf9bb95b541a51224af4484ded22ccb4e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathlog-function-javascript"></a>Math.log 函数 (JavaScript)
返回自然对数 (基`e`) 的数量。  
  
## <a name="syntax"></a>语法  
  
```  
Math.log(number)   
```  
  
#### <a name="parameters"></a>参数  
 数值  
 数字。  
  
## <a name="return-value"></a>返回值  
 如果`number`为正，此函数将返回数字的自然对数。 如果`number`为负，此函数将返回`NaN`。 如果`number`为 0，此函数将返回`-Infinity`。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用此函数。  
  
```JavaScript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Math.sqrt 函数](../../javascript/reference/math-sqrt-function-javascript.md)