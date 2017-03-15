---
title: "CA1814：与多维数组相比，首选使用交错的数组 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1814：与多维数组相比，首选使用交错的数组
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|类别|Microsoft.Performance|  
|是否重大更改|是|  
  
## 原因  
 成员被声明为多维数组。  
  
## 规则说明  
 交错数组是元素为数组的数组。  构成元素的数组可以是不同的大小，以减少某些数据集的浪费空间。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请将多维数组更改为交错数组。  
  
## 何时禁止显示警告  
 如果多维数组不会浪费空间，则可以禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示交错数组和多维数组的声明。  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]