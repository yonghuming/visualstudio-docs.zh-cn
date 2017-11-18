---
title: "Math.round 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Math.round 函数 (JavaScript)
返回提供的数值表达式的舍入为最接近的整数。  
  
## <a name="syntax"></a>语法  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>备注  
 所需`number`自变量是值被舍入到最接近的整数。  
  
 为正数，如果的小数部分`number`为 0.5 或更高版本，返回的值等于最小的整数大于`number`。 如果小数部分小于 0.5，返回值小于最大整数或等于`number`。  
  
 对于负号，如果小数部分是正好-0.5，则返回值是大于数的最小整数。  
  
 例如，`Math.round(8.5)`返回 9，但`Math.round(-8.5)`返回-8。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [Math.random 函数](../../javascript/reference/math-random-function-javascript.md)