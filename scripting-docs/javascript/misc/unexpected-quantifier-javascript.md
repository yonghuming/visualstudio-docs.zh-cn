---
title: "意外的限定符 (JavaScript) |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>意外的限定符 (JavaScript)
当撰写正则表达式搜索模式时，你将创建非法重复重模式元素。 例如，模式  
  
```  
/^+/  
```  
  
 是非法的因为元素 ^ （输入开头） 不能具有重复因素。 下表列出的元素，不能具有重复因素。  
  
|元素|描述|  
|-------------|-----------------|  
|^|输入的开头|  
|$|输入结束|  
|\b|在单词边界|  
|\B|非字边界|  
|*|零个或多个重复|  
|+|一个或多个重复|  
|?|零个或一个重复|  
|{n}|重复 n 次|  
|{n}|n 次或多次重复|  
|{n，m}|从 n 到 m 重复，（含）|  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   请确保您的搜索模式元素包含仅合法重复因素。  
  
## <a name="see-also"></a>另请参阅  
 [正则表达式对象](../../javascript/reference/regular-expression-object-javascript.md)   
 [正则表达式语法 (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)