---
title: "Math.clz32 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Math.clz32 函数 (JavaScript)
返回数字的 32 位二进制表示形式中的前导零位数。  
  
## <a name="syntax"></a>语法  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>备注  
 如果 `number` 为 0，则结果将为 32。 如果 `number` 的 32 位二进制编码的最高有效位为 1，则结果将为 0。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**: [Math 对象](../../javascript/reference/math-object-javascript.md)