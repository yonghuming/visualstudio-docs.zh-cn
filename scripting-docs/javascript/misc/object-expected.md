---
title: "缺少对象 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="object-expected"></a>缺少对象
你尝试调用了 `Object` 类型以外的对象上的方法或属性，或在需要 `Object` 时传递了 `Object` 类型以外的参数。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   仅调用类型为 `Object` 的对象上的方法或属性。  
  
-   如果非对象参数发生错误，则传递类型为 `Object` 的对象。  
  
-   检查是否正在调用未定义的或 null 引用而不是类型为 `Object` 的对象。  
  
     例如，如果以下代码的 myVar 上出现此错误：  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     可改用以下代码：  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [Object 对象](../../javascript/reference/object-object-javascript.md)   
 [对象和数组](../../javascript/objects-and-arrays-javascript.md)