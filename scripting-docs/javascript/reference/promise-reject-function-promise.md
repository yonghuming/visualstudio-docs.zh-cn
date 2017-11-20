---
title: "Promise.reject 函数 （承诺） |Microsoft 文档"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Promise.reject 函数（承诺）
创建新的已拒绝承诺，其结果等于传入的自变量。  
  
## <a name="syntax"></a>语法  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>参数  
 `r`  
 必需。 承诺遭到拒绝的原因。  
  
## <a name="remarks"></a>备注  
 当返回被拒绝的承诺时，运行 `then` 或 `catch` 方法的错误处理函数。  
  
## <a name="example"></a>示例  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Promise 对象](../../javascript/reference/promise-object-javascript.md)