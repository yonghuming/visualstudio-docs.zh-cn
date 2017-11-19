---
title: "缺少枚举器对象 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485e6e387f07fd3a54727f5f8e08c0a00743c6d9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-expected"></a>缺少枚举器对象
你尝试调用**Enumerator.prototype.atEnd、 Enumerator.prototype.item、 Enumerator.prototype.moveFirst，**或**Enumerator.prototype.moveNext**其他类型的对象上的方法比`Enumerator`。 调用此类型的对象的类型必须为`Enumerator`。 下面是代码的一个违反此规则示例：  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   仅调用**Enumerator.prototype.atEnd**， **Enumerator.prototype.item**， **Enumerator.prototype.moveFirst**，或**Enumerator.prototype.moveNext**类型的对象上的方法`Enumerator`。 若要查明你的对象是`Enumerator`对象，请使用：  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [Enumerator 对象](../../javascript/reference/enumerator-object-javascript.md)