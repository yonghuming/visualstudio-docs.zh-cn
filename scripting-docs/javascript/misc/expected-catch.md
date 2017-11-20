---
title: "预期 &#39; catch &#39; |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>预期 &#39; catch &#39;
使用异常处理**重**阻止，但没有编写关联**捕获**语句。 异常处理机制要求可能会失败，以及如果发生异常，不应执行的代码的代码被包装到**重**块。 从引发异常**重**阻止使用**引发**语句，并捕获外部**重**块与一个或多**捕获**语句。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   添加关联**捕获**块。  
  
-   请尝试使用**最后**阻止而不是**捕获**块。  
  
## <a name="see-also"></a>另请参阅  
 [try … catch...最后语句](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [错误对象](../../javascript/reference/error-object-javascript.md)