---
title: "预期的十六进制数字 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="expected-hexadecimal-digit"></a>应为十六进制数字
你创建的不正确的 Unicode 转义序列。 Unicode 转义序列开头 \u 后, 跟完全四个十六进制数字 （没有更多且不小于）。 Unicode 十六进制位只能包含数字 0-9、 大写字母 A 到 F 和小写字母 a-f。 下面的示例演示格式正确的 Unicode 转义序列。  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请确保你 Unicode 十六进制数字开头 \u、 包含数字 0-9、 大写字母 A 到 F，小写字母 a-f;和划分为四位数字。  
  
    > [!NOTE]
    >  如果你想要在字符串内，使用 \u 文本，然后使用两个反斜杠 (\\\u)-一个用于将第一个反斜杠转义。  
  
## <a name="see-also"></a>另请参阅  
 [数据类型](../../javascript/data-types-javascript.md)