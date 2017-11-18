---
title: "数组长度必须赋值为有限正数 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>数组长度必须赋值为有限正数
设置时**长度**现有属性**数组**对象，你可以指定一个正数值或零不是数组长度。 该错误发生时将值赋给**长度**属性`Array`为负的对象或非数值 (`NaN`)。 请注意，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]会自动将小数数字转换为整个整数。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   将一个正整数分配给 length 属性。 最大整数值 （约为 40 亿） 以外，数组的大小没有上限。 下面的示例演示如何设置的正确方式**长度**属性**数组**对象。  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>另请参阅  
 [使用数组](../../javascript/advanced/using-arrays-javascript.md)