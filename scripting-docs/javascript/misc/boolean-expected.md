---
title: "缺少布尔值 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 600ab26f60c2196ebc682adcffcd6b24c23cd358
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="boolean-expected"></a>缺少布尔值
你尝试调用**Boolean.prototype.toString**或**Boolean.prototype.valueOf**以外的类型的对象上的方法`Boolean`。 调用此类型的对象的类型必须为`Boolean`。 例如：  
  
```JavaScript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   仅调用布尔**。 prototype.toString**或**Boolean.prototype.valueOf**类型的对象上的方法**boolean 类型的值。**  
  
## <a name="see-also"></a>另请参阅  
 [Boolean 对象](../../javascript/reference/boolean-object-javascript.md)   
 [数据类型](../../javascript/data-types-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [复制、传递和比较数据](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)