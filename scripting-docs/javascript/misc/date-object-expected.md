---
title: "缺少日期对象 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-expected"></a>缺少日期对象
你尝试调用**Date.prototype.toString**或**Date.prototype.valueOf**以外的类型的对象上的方法`Date`。 调用此类型的对象的类型必须为`Date`。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   仅调用**Date.prototype.toString**或**Date.prototype.valueOf**类型的对象上的方法`Date`。  
  
## <a name="see-also"></a>另请参阅  
 [Date 对象](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [内部对象](../../javascript/intrinsic-objects-javascript.md)