---
title: "isFinite 函数 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="isfinite-function-javascript"></a>isFinite 函数 (JavaScript)
确定提供的数量是有限的。  
  
## <a name="syntax"></a>语法  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>备注  
 所需`number`自变量是任何数字值。  
  
 `isFinite`函数返回`true`如果`number`是任何值，而不`NaN`、 负无穷大或正无穷。 在这三种情况下，它将返回**false**。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **适用于**:[全局对象](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [isNaN 函数](../../javascript/reference/isnan-function-javascript.md)