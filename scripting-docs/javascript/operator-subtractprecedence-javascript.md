---
title: "运算符优先级 (JavaScript) | Microsoft Docs"
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
  - "运算符优先级"
  - "优先级顺序"
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 运算符优先级 (JavaScript)
运算符优先级描述了在计算表达式时执行运算的顺序。  先执行具有较高优先级的运算，然后执行较低优先级的运算。  例如，先执行相乘，再执行相加。  
  
## [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 运算符  
 下表列出了 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 运算符，并按优先级顺序从高到低排列。  具有相同优先级的运算符按从左至右的顺序计算。  
  
|运算符|说明|  
|---------|--------|  
|.\[ \] \( \)|字段访问、数组索引、函数调用和表达式分组|  
|\+\+ \-\- \- ~ \! delete new typeof void|一元运算符、返回数据类型、对象创建、未定义的值|  
|\* \/ %|相乘、相除、求余数|  
|\+ \- \+|相加、相减、字符串串联|  
|\<\< \>\> \>\>\>|移位|  
|\< \<\= \> \>\= instanceof|小于、小于或等于、大于、大于或等于、是否为特定类的实例|  
|\=\= \!\= \=\=\= \!\=\=|相等、不相等、全等，不全等|  
|&|按位“与”|  
|^|按位“异或”|  
|&#124;|按位“或”|  
|&&|逻辑“与”|  
|&#124;&#124;|逻辑“或”|  
|?:|条件运算|  
|\= *OP*\=|赋值、赋值运算（如 \+\= 和 &\=）|  
|,|多个计算|  
  
 圆括号用于改变由运算符优先级确定的计算顺序。  这就是说，先计算完圆括号内的表达式，然后再将它的值用于表达式的其余部分。  
  
 例如：  
  
```javascript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 第一个表达式中有 3 个运算符：\=、\* 和 \+。  按照运算符优先级规则，按以下顺序计算：\*、\+、\=（78 \* 96 \= 7488、7488 \+ 3 \= 7491）。  
  
 在第二个表达式中，先计算 \( \) 运算符，因此，先计算加法表达式，再计算乘法表达式（9 \+ 3 \= 12，12 \* 78 \= 936）。  
  
 以下示例演示包括多个运算符并解析为 `true` 的语句。  
  
```javascript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 运算符按以下顺序计算：用于分组的 \( \)、\*、\+（分组内）、函数中的 "."、函数中的 \( \)、\/、\=\=、\=\=\= 和 &&。