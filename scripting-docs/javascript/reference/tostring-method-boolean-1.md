---
title: "toString 方法 （布尔） 1 |Microsoft 文档"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17dd9503e4e09aafca3d153662bf7487538cda3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-boolean-1"></a>toString 方法 （布尔） 1
返回对象的字符串表示形式。  
  
## <a name="syntax"></a>语法  
  
```  
  
boolean.toString()  
```  
  
## <a name="parameters"></a>参数  
 `boolean`  
 必需。 要为其获取的字符串表示一个对象。  
  
## <a name="return-value"></a>返回值  
 如果布尔值为`true`，返回"true"。 否则，返回"false"。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用**toString**方法。  
  
```JavaScript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]