---
title: "预期 &#39;) &#39;在正则表达式 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>预期 &#39;) &#39;在正则表达式 (JavaScript)
你试图创建正则表达式捕获、 断言或组，但不是包括的右括号。 括号具有正则表达式中有多种用途。 它们用于捕获子表达式，以指定断言，或将模式组合在一起，以便可作为单个单元通过视为项的主要原因是，*，+，？，依次类推。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   添加最右边的右括号。  
  
    > [!NOTE]
    >  如果你想要匹配单个括号，对其进行转义以反斜杠- \\(以便它不被视为特殊字符- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)