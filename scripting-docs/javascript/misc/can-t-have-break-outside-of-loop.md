---
title: "可以 &#39; t 具有 &#39; 中断 &#39;位于循环外 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>可以 &#39; t 具有 &#39; 中断 &#39;位于循环外
你尝试使用**中断**位于循环外的关键字。 **中断**关键字用于终止循环或`switch`语句。 它必须嵌入在正文中的循环或`switch`语句。 但是，**标签**可以按照 break 关键字。  
  
```  
break labelname;  
```  
  
 您只需要的标记的窗体**中断**关键字，当你使用嵌套循环或`switch`语句和需要中断不是最里面的循环。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请确保**中断**关键字出现在封闭的循环或交换机语句内。  
  
## <a name="see-also"></a>另请参阅  
 [break 语句](../../javascript/reference/break-statement-javascript.md)   
 [控制程序流](../../javascript/controlling-program-flow-javascript.md)   
 [脚本疑难解答](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)