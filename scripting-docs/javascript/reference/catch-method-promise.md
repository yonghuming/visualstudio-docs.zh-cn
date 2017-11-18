---
title: "catch 方法 （承诺） |Microsoft 文档"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="catch-method-promise"></a>catch 方法（承诺）
允许你指定承诺遭到拒绝时要执行的工作。  
  
## <a name="syntax"></a>语法  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>参数  
 `promise`  
 必需。 Promise 对象。  
  
 `onRejected`  
 必需。 在承诺遭到拒绝时要运行的错误处理程序函数。  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 在下面的代码示例中，对超时的首次调用在 5000 ms 后返回。 在此代码中，承诺遭到拒绝且运行错误处理程序函数。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]