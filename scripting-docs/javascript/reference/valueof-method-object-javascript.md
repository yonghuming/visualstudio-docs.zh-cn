---
title: "valueOf 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>valueOf 方法 (Object) (JavaScript)
返回指定对象的基元值。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>备注  
 所需`object`引用是任何内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象。  
  
 `valueOf`方法为每个以不同方式定义内部[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]对象。  
  
|对象|返回值|  
|------------|------------------|  
|数组|返回的数组实例。|  
|Boolean|布尔值。|  
|日期|以 UTC 1970 年 1 月 1 日午夜算起的毫秒为单位存储的时间值。|  
|函数|该函数本身。|  
|数字|数值。|  
|对象|对象本身。 这是默认设置。|  
|String|字符串值。|  
  
 **数学**和`Error`的对象不具有`valueOf`方法。  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **适用于**:[数组对象](../../javascript/reference/array-object-javascript.md)&#124;[Boolean 对象](../../javascript/reference/boolean-object-javascript.md)&#124;[日期对象](../../javascript/reference/date-object-javascript.md)&#124;[函数对象](../../javascript/reference/function-object-javascript.md)&#124;[编号对象](../../javascript/reference/number-object-javascript.md)&#124;[Object 对象](../../javascript/reference/object-object-javascript.md)&#124;[的字符串对象](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toString 方法 (Object)](../../javascript/reference/tostring-method-object-javascript.md)