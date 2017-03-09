---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference 函数"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
与相同 [adjacent\_difference](../Topic/adjacent_difference.md), ，但允许使用未检查迭代器作为输出迭代器时 \_SECURE\_SCL \= 1 定义。`unchecked_adjacent_difference` 在中定义 `stdext` 命名空间。  
  
> [!NOTE]
>  此算法是标准 C\+\+ 库的 Microsoft 扩展。 使用此算法实现的代码将不可移植。  
  
## 语法  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### 参数  
 `_First`  
 输入迭代器，此迭代器在其中元素与各自前一元素不同的输入范围内或从中通过其他指定二元运算来操作值对的输入范围内发现第一个元素。  
  
 `_Last`  
 输入迭代器，此迭代器在其中元素与各自前一元素不同的输入范围内或从中通过其他指定二元运算来操作值对的输入范围内发现最后一个元素。  
  
 `_Result`  
 输出迭代器，此迭代器在存储一系列差值或指定运算结果的目标范围内发现第一个元素。  
  
 `_Binary_op`  
 在用于替换差分程序中减法运算的通用运算中应用的二元运算。  
  
## 返回值  
 发现目标范围末尾的输出迭代器︰ `_Result` \+ \(`_Last` \- `_First`\)。  
  
## 备注  
 请参阅 [adjacent\_difference](../Topic/adjacent_difference.md) 有关代码示例。  
  
 检查迭代器的详细信息，请参阅 [经过检查的迭代器](/visual-cpp/standard-library/checked-iterators)。  
  
## 要求  
 **标头：**\<numeric\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)