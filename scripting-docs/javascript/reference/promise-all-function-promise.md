---
title: "Promise.all 函数 （承诺） |Microsoft 文档"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Promise.all 函数（承诺）
联接两个或更多承诺，并且仅在所有指定承诺均完成或被拒绝时返回。  
  
## <a name="syntax"></a>语法  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>参数  
 `func1`  
 必需。 返回承诺的函数。  
  
 `func2`  
 必需。 返回承诺的函数。  
  
 `funcN`  
 可选。 返回承诺的一个或多个函数。  
  
## <a name="remarks"></a>备注  
 返回的结果是由已完成承诺返回的值构成的数组。 如果一个联接的承诺被拒绝，则 `Promise.all` 立即返回拒绝承诺的原因（所有其他返回值将被丢弃）。  
  
## <a name="example"></a>示例  
 在此代码中，对超时的首次调用在 5000 ms 后返回。 完成处理程序调用 `Promise.all`，它仅在对超时的两次调用均完成或被拒绝时返回。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)