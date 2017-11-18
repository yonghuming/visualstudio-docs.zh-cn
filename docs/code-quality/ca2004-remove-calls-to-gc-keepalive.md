---
title: "CA2004： 移除对 GC 调用。KeepAlive |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004：移除对 GC.KeepAlive 的调用
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|类别|Microsoft.Reliability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 类使用`SafeHandle`但仍包含对的调用`GC.KeepAlive`。  
  
## <a name="rule-description"></a>规则说明  
 如果将转换为`SafeHandle`使用情况，删除对所有调用`GC.KeepAlive`（对象）。 在这种情况下，类应该不需要调用`GC.KeepAlive`，假定它们没有终结器，但依赖于`SafeHandle`为它们完成 OS 句柄。  尽管对的调用中将保留成本`GC.KeepAlive`可能可以忽略不计性能，感知，调用`GC.KeepAlive`必要或不足以解决可能不再存在的问题将使代码更加难以进行的生存期维护。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 移除对的调用`GC.KeepAlive`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 仅当不从技术上讲正确，将转换为可以禁止显示此警告`SafeHandle`类中的使用情况。