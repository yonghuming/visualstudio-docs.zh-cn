---
title: "使用数组 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "数组 [JavaScript]"
  - "数组 [JavaScript], 对象"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 使用数组 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的数组是*稀疏的*。  即，如果有一个包含三个编号分别为 0、1 和 2 的元素的数组，则可以创建元素 50，而不必担心元素 3 到 49。  如果数组有一个自动长度变量（有关数组长度的自动监视的说明，请参见[内部对象](../../javascript/intrinsic-objects-javascript.md)），则长度变量将设置为 51 而不是 4。  可以创建其中的元素编号之间无间隙的数组，但您不需要这样做。  
  
 在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中，对象和数组之间几乎相同。  它们之间的两个主要差异是：非数组对象没有自动长度属性；而数组没有对象的属性和方法。  
  
## 寻址数组  
 使用中括号 \(\[\]\) 寻址数组，如以下示例所示。  中括号将一个数值或一个计算结果为整数的表达式括起来。  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## 作为关联数组的对象  
 通常使用点运算符“.”访问对象的属性。  例如，  
  
```javascript  
myObject.aProperty  
```  
  
 在此示例中，属性名为标识符。  您也可以使用索引运算符 \(\[\]\) 来访问对象的属性。  在此情况下，您将对象视为其中的数据值与字符串关联的*关联数组*。  例如，  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 索引运算符通常与访问数组元素关联。  在将其用于对象时，索引是表示属性名的字符串文本。  
  
 请注意两种对象属性访问方式之间的重要差异。  
  
1.  无法像操作数据一样操作被视为标识符（点 \(.\) 语法）的属性名。  
  
2.  可以像操作数据一样操作被视为索引（括号 \(\[\]\) 语法）的属性名。  
  
 如果您在运行时之前不知道属性名称将是什么（例如，当您基于用户输入构造对象时），此差异将显得十分有用。  若要从关联数组中提取所有属性，必须使用 `for…in` 循环。