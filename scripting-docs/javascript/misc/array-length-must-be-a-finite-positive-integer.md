---
title: "数组长度必须为有限正整数 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6589bd2e9bb4acbec5f169087a49e64417dfae7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>数组长度必须为有限正整数
正在调用**数组**与不是整数数量 （包含的零和设置正整数的整数） 的自变量的构造函数。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   创建一个新时仅使用正整数`Array`对象。 如果你想要创建一个包含单个元素，不是一个整数数组，以执行此操作两步过程。 首先创建一个包含一个元素数组，然后将值放入第一个元素 (array[0])。 下面是一个示例，将生成此错误。  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     下面的示例演示具有单个数值元素指定数组的正确方法。  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     最大整数值 （约为 40 亿） 以外，数组的大小没有上限。  
  
## <a name="see-also"></a>另请参阅  
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)