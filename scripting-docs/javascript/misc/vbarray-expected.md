---
title: "缺少 VBArray |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b07c5e08e4178c9c31045317627424f5192f5e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-expected"></a>缺少 VBArray
提供对象时不 Visual Basic safeArray，一个期望值。  
  
```  
new VBArray(safeArray);  
```  
  
 VBArray 是只读的，不能直接创建。 SafeArray 自变量是一个 VBArray 值，和之前，必须获取一个 VBArray 值传递给`VBArray`构造函数。 只有从现有的 ActiveX 或其他对象进行检索，才能获取该值。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   确保仅传递**VBArray**对象添加到**VBArray**构造函数。  
  
## <a name="see-also"></a>另请参阅  
 [VBArray 对象](../../javascript/reference/vbarray-object-javascript.md)   
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)