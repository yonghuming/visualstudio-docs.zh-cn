---
title: "CA1821： 移除空终结器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords: CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afe1c05ff76a2b4c37296ef6a534e37a5d1229b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821：移除空的终结器
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一个类型实现一个为空、 调用仅基类型终结器，或只有条件地发出方法调用的终结器。  
  
## <a name="rule-description"></a>规则说明  
 应尽可能避免终结器，因为跟踪对象生存期会产生额外的性能系统开销。 它收集对象之前，垃圾回收器将运行终结器。 这意味着两个集合，将需要回收该对象。 空的终结器会产生此增加的开销没有任何优势。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 移除空终结器。 如果需要调试终结器，则请将括在整个终结器`#if DEBUG / #endif`指令。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止显示此规则的消息。 取消终止失败会降低性能，并不提供任何好处。  
  
## <a name="example"></a>示例  
 下面的示例演示应删除空终结器，应包含在终结器`#if DEBUG / #endif`指令和使用一个终结器`#if DEBUG / #endif`指令正确。  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]