---
title: "Throw 必须跟在同一源行表达式 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>同一源行中 throw 之后必须有表达式
你使用`throw`关键字，但没有按照它的表达式相同的源行。 A`throw`语句由两部分组成：`throw`关键字后, 跟要引发的表达式。 例如：  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 你无法拆分这两个组件。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请确保`throw`关键字和要引发的表达式都显示在同一行。  
  
## <a name="see-also"></a>另请参阅  
 [错误对象](../../javascript/reference/error-object-javascript.md)   
 [throw 语句](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)