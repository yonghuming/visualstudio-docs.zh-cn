---
title: "Math.sign 函数 (JavaScript) |Microsoft 文档"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cae32118f2265e02c67592facff8e49e8edd633
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="mathsign-function-javascript"></a>Math.sign 函数 (JavaScript)
返回数字符号，它指示数字为正数、负数还是 0。  
  
## <a name="syntax"></a>语法  
  
```  
Math.sign(number)  
```  
  
## <a name="remarks"></a>备注  
 所需的 `number` 参数是一个需要符号的数值表达式。  
  
 返回值为下列之一：  
  
-   如果 `number` 是 `NaN`，则为 `NaN`。  
  
-   -0，如果`number`是-0。  
  
-   如果 `number` 是 +0，则为 +0。  
  
-   -1，如果`number`为负和 not-0。  
  
-   如果 `number` 是正数且不为 +0，则为 +1。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]