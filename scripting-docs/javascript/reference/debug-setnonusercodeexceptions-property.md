---
title: "Debug.setNonUserCodeExceptions 属性 |Microsoft 文档"
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
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="debugsetnonusercodeexceptions-property"></a>Debug.setNonUserCodeExceptions 属性
确定是否要为用户未处理调试器时被视为此作用域中的任何 try catch 块。 可以被归类为可引发，用户未处理或未经处理的异常。  
  
 如果此属性设置为`true`在给定范围中，调试器然后，可以确定采取某种操作 （例如，中断） 上如果开发人员想要在用户未处理异常时中断，在该作用域内引发的异常。 如果此属性设置为`false`是相同好像永远不会设置该属性。  
  
 有关调试的详细信息，请参阅[活动脚本调试概述](http://go.microsoft.com/fwlink/p/?LinkId=249469)。  
  
## <a name="syntax"></a>语法  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>示例  
 下面的代码演示如何设置此属性。  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]