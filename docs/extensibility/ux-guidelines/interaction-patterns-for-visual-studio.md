---
title: "Visual Studio 的交互模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Visual Studio 的交互模式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## 概述  
 一种设计模式，一般情况下，是设计的可以应用在特定情况下，若要解决问题的约束的组相似的核心。 功能和系统设计器使用这些设计模式作为起始点，然后可适用于其特定的情况。  
  
 Visual Studio 提供了构建新功能时，应考虑的常见交互模式的库。 有两个核心上下文，我们设计模式: Visual Studio 客户端 \(devenv\) 和 Visual Studio Online。 对于某些设计问题，是适用于所有情况下的无处不在模式。 在许多情况下，但是，解决方案可能会有所不同的浏览器和，托管在客户端应用程序中为其提供的用户界面。  
  
### Visual Studio 客户端模式类型  
  
|模式类型|描述|示例|  
|----------|--------|--------|  
|**应用程序级模式**|普遍适用于该应用程序，确定或显示应用程序上下文中，并包含其中的复合和控件模式的高级模式|-   工具窗口<br />-   文档窗口|  
|**复合模式**|可能会跨越应用程序模式的常见模式或识别的模式的不同配置的几种控件组成|-   视图切换<br />-   列表生成器<br />-   显示数据<br />-   通知<br />-   验证<br />-   选择模型|  
|**控件模式**|有关如何低级别的控件的具体信息会表现出的行为|-   树视图<br />-   网格控件中编辑|  
  
## 应用程序模式  
 在高级别中，Visual Studio 界面包含多个窗口、 对话框、 命令和在单个 IDE 中的工具栏。 Visual Studio 层次结构确定上下文和驱动器菜单。 IDE 的用户界面的关键的集成点是文档窗口、 工具窗口、 项目、 命令结构，文本编辑器、 工具箱、 属性窗口中和工具 \> 选项。  
  
 有基本的用法模式为每个用户界面中的 IDE 的关键集成点:  
  
-   [菜单和 Visual studio 命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio 的应用程序模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [窗口的交互](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [工具窗口](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [文档编辑器约定](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [项目](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## 公共控件模式  
 控件模式主要是关于个别控件预期行为。 这是一个在其中的一致性是最关键的区域。  
  
 Visual Studio 中的最常见控件应遵循的桌面 Windows 准则。 我们的指导原则只包括我们需要增加与 Visual Studio 特有的交互或在其中我们取代这些准则完全以便量身定制以满足我们经验丰富的用户的需求的 Visual Studio 的位置的通用约定领域。  
  
-   [用于 Visual Studio 的常用控件模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [公共控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [文本控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [按钮和超链接](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## 复合模式  
 有多种方式让用户希望能够完成的任务。 只要有可能，功能应设计为使用这些模式为交互和可视化设计。  
  
 尽管有许多的复合模式，在 Visual Studio 中，一些最重要的方面的一致性是:  
  
-   [Visual Studio 的复合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [对象上的用户界面和查看](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [选择模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [持久性和保存设置](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [触摸输入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)