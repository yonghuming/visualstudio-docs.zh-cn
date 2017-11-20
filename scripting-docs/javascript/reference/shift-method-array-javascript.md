---
title: "shift 方法 (Array) (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>shift 方法 (Array) (JavaScript)
从数组中移除第一个元素并将返回该元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>参数  
 所需`arrayObj`引用是`Array`对象。  
  
## <a name="return-value"></a>返回值  
 返回从数组中删除的元素。  
  
## <a name="remarks"></a>备注  
 下面的示例演示 `shift` 方法的用法。  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [unshift 方法 (Array)](../../javascript/reference/unshift-method-array-javascript.md)