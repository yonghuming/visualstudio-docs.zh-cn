---
title: "valueOf 方法 (Boolean) |Microsoft 文档"
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
ms.assetid: ac6ad343-7663-406a-a2b7-4cc5025ca3d6
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c36eda63fb38886df4d8bffec7cfdbb6c6d05eb8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-boolean"></a>valueOf 方法 (Boolean)
返回指定的布尔值的基元值。  
  
## <a name="syntax"></a>语法  
  
```  
  
boolean.valueOf()  
```  
  
## <a name="return-value"></a>返回值  
 布尔值基元值 （true 或 false）。  
  
## <a name="remarks"></a>备注  
 下面的代码演示如何使用此方法。  
  
```JavaScript  
var bool = new Boolean("true");  
var s = bool.valueOf();  
document.write(s);  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]