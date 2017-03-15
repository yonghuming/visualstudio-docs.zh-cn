---
title: "Visual Studio 扩展性体系结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, 环境模型"
  - "环境模型, Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Visual Studio 扩展性体系结构
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成 \(IDE\)开发环境是框架承载的 Vspackage 和使其更易于交换共享服务。  此示例是 IDE 实现用户 \(UI\)界面 \(ui\)。  IDE 提供容器窗口和默认工具栏和菜单。  它还提供了一些 UI 可编程的丰富的 COM 基础结构。  处理和路由模式的完整命令为用户提供易于访问现有和安装的命令设置的开放式的帧。  
  
## 扩展性的体系结构  
 下图显示 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 扩展性的体系结构。  请注意软件应用程序的概念不存在。  相反， IDE 中承载软件组件，调用 Vspackage，提供应用程序功能。  此函数在 IDE 中，反过来，共享作为服务。  Vspackage 提供服务以及其他 Vspackage 使用。  标准 IDE 还提供各种服务，如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>，提供对 IDE 多窗口功能。  
  
 ![环境体系结构图](../extensibility/internals/media/environment.png "environment")  
Visual Studio 体系结构的通用视图  
  
 通知 Vspackage 和服务之间的关系是双向的。  虽然 Vspackage 使用服务由其他提供，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 接口，它们也可以提供自己的服务。  此基于服务的体系结构增大 Microsoft ActiveX 设计器实现的外部，服务有关接口一组执行任务。  从强 COM 角度来看，在单个 COM 类必须实现一个特定服务的任何接口。  
  
 标准 IDE 提供重要服务，例如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>和 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>， Vspackage 使用。  下表列出并描述了一些服务。  有关更多信息，请参见 [使用并提供服务](../extensibility/using-and-providing-services.md)。  
  
|IDE 服务|说明|  
|------------|--------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|提供对处理基本功能、 Vspackage 和注册表的 IDE 服务。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本多窗口和与用户界面相关的功能在 IDE，例如能够创建工具窗口和文档。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供基本的解决方案相关的功能，例如能够枚举项，创建新项目，，并监视项目更改。|  
  
 由于这些紧密集成通过共享服务的交互， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 和 Vspackage 依赖关系紧密的。  但是，尽管它们接近的交互它们有不同的责任。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 到负责以下任务:  
  
-   提供用于外部 Vspackage 使用的重要服务。  
  
-   提供的可编程接口，从而启用与标准 UI 元素的输入。  
  
-   创建 Vspackage 实例作为用户操作要求或其他请求的 Vspackage 服务。  
  
-   提供可以为通信和协调 Vspackage 之间的服务。  
  
-   托管解决方案及其需的文件。  
  
-   提供窗口管理。  
  
-   提供有关路由和命令栏，如菜单、工具栏和上下文菜单。  
  
-   协调的选择、上下文和货币。  
  
 Vspackage 到负责以下任务:  
  
-   执行某些初始化和终止实例。  
  
-   对注册表的信息写入， IDE 使用将相应的 Vspackage 在适当的时间。  
  
-   提供通信所需的与其他 Vspackage 的服务。  
  
-   提供实现为新的项目类型、编辑器和设计器。  
  
-   提供扩展内置 UI 元素，如任务、项目、工具箱项和选项 " 对话框。  
  
## 请参阅  
 [Visual Studio Shell](../extensibility/internals/visual-studio-shell.md)   
 [Vspackage](../extensibility/internals/vspackages.md)   
 [使用并提供服务](../extensibility/using-and-providing-services.md)   
 [如何: 获取服务](../Topic/How%20to:%20Get%20a%20Service.md)