---
title: "CA1020： 避免使用几种类型的命名空间 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c09f3fa7855f2dadfce7a22914c4a7010b84f210
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020：避免使用类型极少的命名空间
|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 在全局命名空间之外的命名空间包含少于五个类型。  
  
## <a name="rule-description"></a>规则说明  
 请确保每个命名空间有一个逻辑组织，并且存在一个有效原因将稀疏填充的命名空间中的类型。 命名空间应包含在大多数情况下一起使用的类型。 当其应用程序互相排斥，类型应位于单独的命名空间。 例如，<xref:System.Web.UI>命名空间包含在 Web 应用程序中使用的类型和<xref:System.Windows.Forms>命名空间包含在中使用类型[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-基于应用程序。 即使两个命名空间都具有控制用户界面各方面的类型，这些类型也并不是旨在用于同一应用程序。 因此，它们位于单独的命名空间中。 请小心命名空间组织也会有所帮助，因为这样可以增加一项功能的可发现性。 通过检查命名空间层次结构，库使用者应该能够找到实现一个功能的类型。  
  
> [!NOTE]
>  设计时类型和权限不应合并到其他命名空间，以符合此原则。 这些类型属于主命名空间下, 自己的命名空间和命名空间应以结尾`.Design`和`.Permissions`分别。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，尝试将合并到单个命名空间包含几个类型的命名空间。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，命名空间不包含与其他命名空间中的类型使用的类型时。