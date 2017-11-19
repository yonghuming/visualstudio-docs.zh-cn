---
title: "CA1822： 将成员标记为静态 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 160b263bde66496bad4f4fcb363852bdb174ff62
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1822-mark-members-as-static"></a>CA1822：将成员标记为 static
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|类别|Microsoft.Performance|  
|是否重大更改|无间断-如果不是程序集外部可见成员而不考虑更改你进行。 非重大更改-如果你只需更改成员的实例成员为`this`关键字。<br /><br /> 中断性-如果从实例成员的成员更改为静态成员，并且它是程序集外部可见。|  
  
## <a name="cause"></a>原因  
 不会访问实例数据的成员未标记为 static (在共享[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。  
  
## <a name="rule-description"></a>规则说明  
 可以将不访问实例数据或不调用实例方法的成员标记为 static（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Shared）。 在将这些方法标记为 static 之后，编译器将向这些成员发出非虚拟调用站点。 发出非虚拟调用站点将禁止在每个调用，以确保当前的对象指针为非 null 的运行时检查。 这可以实现使性能敏感的代码得到显著提高。 在某些情况下，无法访问当前的对象实例表示的正确性问题。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 将标记为静态成员 (或共享中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 或使用 this / Me 方法中的正文，如果适用。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则，以前发布的解决方法将一项重大更改的代码的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)