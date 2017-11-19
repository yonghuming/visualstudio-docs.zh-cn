---
title: "CA1814： 更喜欢通过多维交错数组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa1420ab01426cbfeaaf5d70238df19fde50ea9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814：与多维数组相比，首选使用交错的数组
|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|类别|Microsoft.Performance|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 一个成员声明为多维数组。  
  
## <a name="rule-description"></a>规则说明  
 交错数组是元素为数组的数组。 构成元素的数组可以是不同的大小，以减少某些数据集的浪费空间。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改到交错数组的多维数组。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果多维数组不会浪费空间，禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示交错和多维数组的声明。  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]