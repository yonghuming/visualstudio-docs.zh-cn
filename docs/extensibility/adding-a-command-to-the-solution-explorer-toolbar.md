---
title: "将命令添加到解决方案资源管理器工具栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: "39"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26f5777477617b0bffe008ec92873b852af8fe08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>将命令添加到解决方案资源管理器工具栏
本演练演示如何向其中添加按钮**解决方案资源管理器**工具栏。  
  
 工具栏或菜单上的任何命令在 Visual Studio 中调用一个按钮。 单击按钮时，执行的命令处理程序中的代码。 通常情况下，相关的命令组合在一起以形成一个组。 菜单或工具栏作为容器的组。 优先级确定菜单中或在工具栏上显示组中的单个命令的顺序。 你可以防止通过控制其可见性显示在工具栏或菜单按钮。 中列出的命令`<VisibilityConstraints>`仅在相关联的上下文中出现的.vsct 文件的部分。 可见性不能应用于组中。  
  
 有关菜单、 工具栏命令和.vsct 文件的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
> [!NOTE]
>  使用 XML 命令表 (.vsct) 文件而不是命令表配置 (.ctc) 文件来定义菜单和命令在你的 Vspackage 中的显示方式。 有关详细信息，请参阅 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>使用菜单命令创建扩展  
 创建一个名为的 VSIX 项目`SolutionToolbar`。 添加名为的菜单命令项模板**工具栏按钮**。 有关如何执行此操作的信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>将按钮添加到解决方案资源管理器工具栏  
 本部分演练演示如何向其中添加按钮**解决方案资源管理器**工具栏。 单击该按钮时，运行的回调方法中的代码。  
  
1.  在 ToolbarButtonPackage.vsct 文件中，转到`<Symbols>`部分。 `<GuidSymbol>`节点包含菜单组和命令由包模板生成。 添加`<IDSymbol>`给此节点来声明将保存你的命令的组的元素。  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  在`<Groups>`部分中，现有的组项之后, 你声明的新组在中定义上一步。  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     将父 guid: id 对设置为`guidSHLMainMenu`和`IDM_VS_TOOL_PROJWIN`放该组**解决方案资源管理器**工具栏上，并在设置优先级较高的值将其放在其他命令组的后面。  
  
3.  在`<Buttons>`部分中，更改生成的父 ID`<Button>`条目以反映你在上一步中定义的组。 已修改`<Button>`元素应如下所示：  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  生成项目并启动调试。 实验实例中出现。  
  
     **解决方案资源管理器**工具栏应显示现有按钮右侧的新建命令按钮。 该按钮图标为带删除线。  
  
5.  单击新建按钮。  
  
     程序消息的对话框**ToolbarButtonPackage 内 SolutionToolbar.ToolbarButton.MenuItemCallback()**应显示。  
  
## <a name="controlling-the-visibility-of-a-button"></a>控制按钮的可见性  
 本部分演练演示如何控制工具栏上按钮的可见性。 通过将上下文设置为中的一个或多个项目`<VisibilityConstraints>`部分 SolutionToolbar.vsct 文件的限制按钮出现只有当一个项目均为打开。  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>打开一个或多个项目时显示的按钮  
  
1.  在`<Buttons>`部分的 ToolbarButtonPackage.vsct，将两个命令标志添加到现有`<Button>`元素之间`<Strings>`和`<Icons>`标记。  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible`和`DynamicVisibility`标志必须设置操作中的该条目`<VisibilityConstraints>`部分才会生效。  
  
2.  创建`<VisibilityConstraints>`具有两个部分`<VisibilityItem>`条目。 恰好在结束后放置新节`</Commands>`标记。  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     可见性的每一项表示指定的按钮将显示在其下条件。 若要应用的多个条件，你必须创建多个条目的同一按钮。  
  
3.  生成项目并启动调试。 实验实例中出现。  
  
     **解决方案资源管理器**工具栏不包含带删除线按钮。  
  
4.  打开包含项目的任何解决方案。  
  
     在工具栏上的现有按钮右侧会显示带删除线按钮。  
  
5.  上**文件**菜单上，单击**关闭解决方案**。 从工具栏中，该按钮即消失。  
  
 按钮的可见性控制通过[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]直到加载 VSPackage。 加载 VSPackage 后，由 VSPackage 控制按钮的可见性。  有关详细信息，请参阅[MenuCommands 与。OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)。  
  
## <a name="see-also"></a>另请参阅  
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)