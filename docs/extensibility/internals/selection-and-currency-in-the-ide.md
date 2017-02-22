---
title: "所选内容和在 IDE 中的货币 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "货币，Visual Studio IDE"
  - "IDE 中选择"
  - "所选内容，Visual Studio IDE"
  - "IDE 中货币"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 所选内容和在 IDE 中的货币
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\) 维护有关用户的信息当前所选对象，通过使用所选内容 *上下文*。 与所选内容上下文 Vspackage 可以参与货币跟踪两种方式︰  
  
-   通过传播有关 VSPackages 迁移到 IDE 的货币信息。  
  
-   通过监视在 IDE 中的用户的当前处于活动状态选择。  
  
## 选定内容上下文  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 全局跟踪的 IDE 在其自己的全局选择上下文对象中的货币。 下表显示构成了所选内容上下文的元素。  
  
|元素|描述|  
|--------|--------|  
|当前层次结构|通常当前项目;NULL 当前层次结构表示作为一个整体解决方案是最新。|  
|当前 ItemID|当前层次结构; 内的选定的项当有多个选择在项目的窗口中，则可能出现多个当前项。|  
|当前 `SelectionContainer`|包含一个或多个对象为其属性窗口应显示属性。|  
  
 此外，该环境维护两个全局列表︰  
  
-   活动的用户界面命令标识符的列表  
  
-   当前处于活动状态的元素类型的列表。  
  
### 窗口类型和所选内容  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 将组织为两种常规类型︰ windows:  
  
-   层次结构类型 windows  
  
-   框架窗口，例如工具和文档窗口  
  
 IDE 为上述每种窗口类型以不同的方式跟踪货币。  
  
 最常见的项目类型窗口是解决方案资源管理器，它控制着 IDE。 项目类型窗口跟踪的全局层次结构中和 ItemID 全局选择上下文中，并且窗口中依赖于用户的选择，以确定当前层次结构。 对于项目类型 windows 环境提供全球服务 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, ，直到哪些 Vspackage 可以监视打开的元素的当前值。 此全局服务由驱动浏览在环境中的属性。  
  
 框架窗口，相反，使用该文档在框架窗口内推送 SelectionContext 值 （层次结构\/ItemID\/SelectionContainer 三）。 。 框架窗口使用服务 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 实现此目的。 DocObject 可以推送有效值选择容器中，保留层次结构中的本地值和 ItemID 不变，因为是典型的 MDI 子文档。  
  
### 事件和货币  
 两种类型的事件可能会发生，影响的货币的环境的概念︰  
  
-   传播到全局级别并更改窗口框架选定内容上下文事件。 此类事件的示例包括打开，正在打开的全局工具窗口或正在打开的项目类型工具窗口的 MDI 子窗口。  
  
-   更改跟踪的窗口框架选择上下文中的元素的事件。 示例包括更改 DocObject 内的选择或更改项目类型窗口中的选择。  
  
## 请参阅  
 [选择上下文对象](../../extensibility/internals/selection-context-objects.md)   
 [向用户的反馈](../../extensibility/internals/feedback-to-the-user.md)