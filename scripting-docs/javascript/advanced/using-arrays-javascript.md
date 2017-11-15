---
title: "使用数组 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="using-arrays-javascript"></a>使用数组 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的数组是稀疏型。 即，如果数组中有三个元素，编号为 0、1 和 2，则可以创建元素 50，而无需考虑元素 3 到元素 49。 如果此数组中包含自动长度变量（请参阅[固有对象](../../javascript/intrinsic-objects-javascript.md)查看关于自动监视数组长度的说明），则会将长度变量设置为 51，而非 4。 可以创建元素编号间不存在间隔的数组，但是不会要求必须这样做。  
  
 在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，对象和数组几乎完全相同。 主要的两个区别是非数组对象没有自动长度属性，数组没有对象的属性和方法。  
  
## <a name="addressing-arrays"></a>寻址数组  
 使用方括号 ([]) 为数组寻址，如以下示例所示。 方括号会将数值或计算结果为整数的表达式括起来。  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>作为关联阵列的对象  
 通常使用点运算符“.”访问对象的属性。 例如，  
  
```JavaScript  
myObject.aProperty  
```  
  
 在此示例中，属性名称是一个标识符。 也可以使用索引运算符 ([]) 访问对象的属性。 在此示例中，将对象视为数据值与字符串关联的关联阵列。 例如，  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 索引运算符通常与访问数组元素相关联。 用于访问对象时，索引是表示属性名称的字符串。  
  
 请注意，访问对象属性的两种方法之间存在显著区别。  
  
1.  视作标识符（点 (.) 语法）的属性名称不能作为数据进行操纵。  
  
2.  视作索引（方括号 (.) 语法）的属性名称可以作为数据进行操纵。  
  
 在运行时前不知道属性名称是什么的情况下（例如，根据用户输入构造对象时），这一区别将很有用。 若要从关联阵列中提取所有属性，必须使用 `for...in` 循环。