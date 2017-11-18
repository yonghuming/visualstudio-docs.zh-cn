---
title: "Number.isInteger 函数 （数字） (JavaScript) |Microsoft 文档"
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger 函数（数字）(JavaScript)
返回一个布尔值，该值指示值是否为整数。  
  
## <a name="syntax"></a>语法  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>返回值  
 如果值为整数则为 `true`，否则为 `false`。  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>示例  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```