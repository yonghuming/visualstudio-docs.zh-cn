---
title: "Number.isFinite 函数 （数字） (JavaScript) |Microsoft 文档"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23ff1e80ad71fd9d848f7a0e33628131f5d8014
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="numberisfinite-function-number-javascript"></a>Number.isFinite 函数（数字）(JavaScript)
返回一个布尔值，该值指示值是否为有限数字。  
  
## <a name="syntax"></a>语法  
  
```  
Number.isFinite(numValue)   
```  
  
## <a name="return-value"></a>返回值  
 如果值为 `NaN``+∞` 或 `-∞`，则为 `false`；否则为 `true`。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
  
```JavaScript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **适用于**: [Number 对象](../../javascript/reference/number-object-javascript.md)