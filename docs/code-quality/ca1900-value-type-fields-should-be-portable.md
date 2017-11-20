---
title: "CA1900： 值类型字段应为可移植 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f2d948d78f6b12352a3e4cfcb28aab41db3e873
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900：值类型字段应为可移植字段
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|类别|Microsoft.Portability|  
|是否重大更改|中断性-如果字段可以程序集外可见。<br /><br /> 无间断-如果该字段不是程序集外部可见。|  
  
## <a name="cause"></a>原因  
 此规则检查： 当用显式布局声明的结构封送到 64 位操作系统上的非托管代码时，将是否正确对齐。 Ia-64 不允许访问未对齐的内存和如果不解决此冲突，则进程将崩溃。  
  
## <a name="rule-description"></a>规则说明  
 具有显式布局，包含在 64 位操作系统上的未对齐的字段会导致发生崩溃的结构。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 小于 8 个字节的所有字段都必须是其大小的倍数的偏移量和 8 个字节的字段或更多都必须是 8 的倍数的偏移量。 另一种解决方案是使用`LayoutKind.Sequential`而不是`LayoutKind.Explicit`，如果合理。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 应禁止显示此警告，仅当其出现在错误中。