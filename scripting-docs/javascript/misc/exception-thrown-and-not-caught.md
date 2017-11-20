---
title: "引发了异常且未被捕获 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>引发了异常且未被捕获
你包含`throw`不括在你的代码，但它的语句**重**块，或没有任何关联**捕获**块来捕获错误。 从引发异常**重**阻止使用**引发**语句，并捕获外部**重**块**捕获**语句。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   将可以在引发的异常的代码包含在**重**块，并确保没有相应**捕获**块。  
  
-   请确保你的 catch 语句需要正确形式的异常。  
  
-   如果引发异常，请确保没有另一个相应的 catch 语句。  
  
## <a name="see-also"></a>另请参阅  
 [错误对象](../../javascript/reference/error-object-javascript.md)   
 [throw 语句](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)