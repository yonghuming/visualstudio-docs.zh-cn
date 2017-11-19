---
title: "Ca1030： 在适用处使用事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c07aac3780abc10dd3995b21b5c9636607166f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030：在适用处使用事件
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 公共、 受保护或私有方法名称开头以下项之一：  
  
-   加载项  
  
-   RemoveOn  
  
-   激发  
  
-   引发  
  
## <a name="rule-description"></a>规则说明  
 该规则检测名称通常用于事件的方法。 事件遵循观察者或发布-订阅设计模式;必须将一个对象中的状态更改传送到其他对象时使用它们。 如果一种方法获取调用以响应明确定义的状态更改，则应由事件处理程序调用的方法。 调用该方法的对象应引发事件而不是直接调用该方法。  
  
 在其中用户操作，例如单击按钮会导致一段代码执行的用户界面应用程序中找到事件一些常见示例。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型并不局限于用户界面; 应使用随处必须通信状态将更改为一个或多个对象。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 如果对象的状态更改时调用该方法，则应考虑更改设计以确保使用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 禁止显示此规则的警告，如果该方法并不适用于[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]事件模型。