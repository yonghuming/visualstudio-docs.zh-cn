---
title: "选择和 IDE 中的货币 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 307344a9027e629f08350b77adf99d22d0c127a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="selection-and-currency-in-the-ide"></a>选择和 IDE 中的货币
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE) 维护有关用户的信息当前所选对象，通过选择*上下文*。 与所选内容的上下文中，Vspackage 可以参与货币跟踪两种方式：  
  
-   通过将传播到 IDE Vspackage 的货币信息。  
  
-   通过监视在 IDE 中的用户的当前活动选择。  
  
## <a name="selection-context"></a>选择上下文  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 全局跟踪的在其自己的全局选择上下文对象中的 IDE 货币。 下表显示构成选择上下文的元素。  
  
|元素|描述|  
|-------------|-----------------|  
|当前层次结构|通常当前项目;NULL 当前层次结构指示作为一个整体解决方案是最新。|  
|当前 ItemID|当前层次结构; 内的选定的项当在项目窗口中的多个选择，可以有多个当前项。|  
|当前`SelectionContainer`|包含为其属性窗口应显示属性的一个或多个对象。|  
  
 此外，环境负责维护两个全局列表：  
  
-   Active UI 命令标识符的列表  
  
-   当前处于活动状态的元素类型的列表。  
  
### <a name="window-types-and-selection"></a>窗口类型和所选内容  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 将 windows 组织成两种常规类型：  
  
-   层次结构类型 windows  
  
-   框架窗口，如工具和文档窗口  
  
 IDE 跟踪货币以不同方式为每个这些窗口类型。  
  
 最常见的项目类型窗口是解决方案资源管理器，它 IDE 控制。 项目类型窗口跟踪的全局层次结构和 ItemID 全局选择上下文中，并依赖于用户的选择，以确定当前层次结构的窗口。 对于项目类型 windows 环境提供全局服务<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>，通过的 Vspackage 可以监视打开的元素的当前值。 此全局服务由驱动浏览在环境中的属性。  
  
 框架窗口，另一方面，使用 DocObject 在框架窗口内推送 SelectionContext 值 （层次结构/ItemID/SelectionContainer 三个）。 . 框架窗口使用服务<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>为此目的。 DocObject 可以推送仅选择容器的值将保留层次结构的本地值和 ItemID 不变，典型的 MDI 子文档。  
  
### <a name="events-and-currency"></a>事件和货币  
 两种类型的事件可能会发生，影响的货币的环境的概念：  
  
-   可以传播到全局级别和更改的窗口框架选择上下文的事件。 这种事件的示例包括打开，全局工具窗口打开或正在打开的项目类型工具窗口的 MDI 子窗口。  
  
-   更改跟踪的窗口框架选择上下文中的元素的事件。 示例包括更改 DocObject 内的选择或更改在项目类型的窗口中的选择。  
  
## <a name="see-also"></a>另请参阅  
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [为用户提供反馈](../../extensibility/internals/feedback-to-the-user.md)