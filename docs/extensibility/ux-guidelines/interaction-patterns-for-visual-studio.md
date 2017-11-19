---
title: "Visual Studio 的交互模式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e084ace914f65a9e97307f0a70d6c5e2211be55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio 的交互模式
## <a name="overview"></a>概述  
 设计模式中，一般情况下，是设计的可以在特定情况下，若要解决问题的约束类似集应用的核心。 功能和系统设计器使用这些设计模式作为起始点，然后可适用于其特定的情况。  
  
 Visual Studio 提供生成新的功能时应考虑的常见交互模式的库。 有两个核心上下文我们设计模式： Visual Studio 客户端 (devenv) 和 Visual Studio Online。 对于某些设计问题，没有适用于所有情况下无处不在模式。 在许多情况下，但是，解决方案可能是不同要呈现在浏览器和的客户端应用程序上托管的 ui。  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio 客户端模式类型  
  
|模式类型|描述|示例|  
|------------------|-----------------|--------------|  
|**应用程序级模式**|常见应用程序，确定或显示应用程序上下文，并包含其中的复合和控件模式的高级模式|-工具窗口<br />文档窗口|  
|**复合模式**|可能跨越应用程序模式的常见模式或可识别的模式不同的配置中的多个控件的组成|视图切换<br />列表生成器<br />-显示数据<br />-通知<br />验证<br />选择模型|  
|**控件模式**|有关如何低级别的控件的具体信息被预期行为|树视图<br />编辑网格控件内|  
  
## <a name="application-patterns"></a>应用程序模式  
 在高级别中，Visual Studio 界面包含多个 windows、 对话框、 命令和单个 IDE 中的工具栏。 Visual Studio 层次结构确定上下文和驱动器菜单。 在 IDE 的用户界面的关键集成点是文档窗口、 工具窗口、 项目、 命令结构、 文本编辑器、 工具箱、 属性窗口中和工具 > 选项。  
  
 有为每个用户界面中的关键集成点，在 IDE 的基本用法模式：  
  
-   [Visual Studio 的菜单和命令](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio 的应用程序模式](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [窗口交互](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [工具窗口](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [文档编辑器约定](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [对话框](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [项目](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>常见的控件模式  
 控件模式是主要有关个别控件预期行为。 这是一致性处于最严重的一个区域。  
  
 Visual Studio 中的最常见控件应遵循的桌面 Windows 准则。 我们的指导原则仅包括我们需要增加与 Visual Studio 特定交互或在其中我们取代准则完全为了定制 Visual Studio 以满足我们复杂的用户的需求的位置的通用约定领域。  
  
-   [Visual Studio 的公共控件模式](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [常见控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [文本控件](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [按钮和超链接](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>复合模式  
 有大量的用户预期来完成任务的方式。 只要有可能，功能应设计为使用这些模式用于交互和可视设计。  
  
 尽管有许多的复合模式，在 Visual Studio 中，最重要的一些方面一致性是：  
  
-   [Visual Studio 的复合模式](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [对象上的 UI 和扫视](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [所选内容模型](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [持久性和保存设置](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [触摸屏输入](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)