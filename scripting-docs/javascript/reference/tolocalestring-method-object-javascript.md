---
title: "toLocaleString 方法 (Object) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString 方法 (Object) (JavaScript)
返回日期转换为使用当前区域设置的字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>备注  
 所需`dateObj`是下列任一`Date`对象。  
  
 `toLocaleString`方法返回`String`对象，其中包含在当前区域设置的长默认格式写入日期。  
  
-   对于 1999年公元 1601年和之间的日期，在日期格式为根据用户的控制面板区域设置。  
  
-   超出此范围的默认格式的日期**toString**使用方法。  
  
 例如，在美国，`toLocaleString`返回"01/05/96 00:00:00"为 1 月 5 日。 在欧洲的该命令返回"05/01/96 00:00:00"相同的日期，为欧洲的约定将月前的一天。  
  
> [!NOTE]
>  `toLocaleString`应仅用于向用户显示结果它应绝不会用作基础计算脚本中返回的结果是特定于计算机。  
  
## <a name="example"></a>示例  
 下面的示例演示 `toLocaleString` 方法的用法。  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **适用于**:[数组对象](../../javascript/reference/array-object-javascript.md)&#124;[日期对象](../../javascript/reference/date-object-javascript.md)&#124;[编号对象](../../javascript/reference/number-object-javascript.md)&#124;[Object 对象](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>另请参阅  
 [toLocaleDateString 方法 (Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)