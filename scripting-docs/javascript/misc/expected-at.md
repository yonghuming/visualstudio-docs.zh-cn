---
title: "预期 &#39; @&#39; |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939"></a>预期 &#39; @&#39;
尝试创建一个变量以与使用的条件编译语句一起使用`@set`语句，但是没有按照 at 符号"**@**"之前的变量的名称。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   添加 at 符号"**@**"紧接在变量名称之前。 例如:   
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [@set语句](../../javascript/reference/at-set-statement-javascript.md)   
 [条件编译](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件编译变量](../../javascript/advanced/conditional-compilation-variables-javascript.md)