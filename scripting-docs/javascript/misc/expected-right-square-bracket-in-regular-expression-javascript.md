---
title: "预期 &#39;]&#39;在正则表达式 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>预期 &#39;]&#39;在正则表达式 (JavaScript)
您试图为正则表达式匹配项，创建字符类，但不是包括右括号。 可以将它们放置在方括号内，到字符类组成单个文本的字符组合。 字符类匹配包含任何一个字符。 例如，/ [abc] / 匹配任何一个字母"a"、"b"或"c"。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   添加到正则表达式的右括号。  
  
    > [!NOTE]
    >  如果你想要匹配单个大括号，对其进行转义以反斜杠- \\[-这样，它不被视为特殊字符[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)