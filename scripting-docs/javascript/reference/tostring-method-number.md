---
title: "toString 方法 (Number) |Microsoft 文档"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-number"></a>toString 方法（数字）
返回数字的字符串表示。  
  
## <a name="syntax"></a>语法  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>参数  
 `number`  
 必需。 要以字符串形式表示的数字。  
  
## <a name="return-value"></a>返回值  
 数字字符串表示形式。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**toString**与大量的方法。  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]