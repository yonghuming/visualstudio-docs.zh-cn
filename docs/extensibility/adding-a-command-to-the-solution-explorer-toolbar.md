---
title: "将命令添加到解决方案资源管理器工具栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5d6e1e597db52e4ba087cd358f1d2bdbd5f208f
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>将命令添加到解决方案资源管理器工具栏
本演练演示如何向其中添加按钮**解决方案资源管理器**工具栏。  
  
 在 Visual Studio 中，工具栏或菜单上的任何命令称为一个按钮。 当单击按钮时，将执行的命令处理程序中的代码。 通常情况下，相关的命令被组合在一起以形成一个组。 菜单或工具栏充当容器的组。 优先级确定的菜单中或在工具栏上显示组中的单个命令的顺序。 您可以防止一个按钮工具栏或菜单上显示通过控制其可见性。 中列出的命令`<VisibilityConstraints>`仅在相关联的上下文中会出现.vsct 文件的部分。 可见性不能应用于组。  
  
 有关菜单、 工具栏命令和.vsct 文件的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
> [!NOTE]
>  使用 XML 命令表 (.vsct) 文件而不是命令表配置 (.ctc) 文件来定义菜单和命令在您 VSPackages 迁移中的显示方式。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>使用菜单命令创建扩展  
 创建一个名为的 VSIX 项目`SolutionToolbar`。 添加一个名为的菜单命令项模板**工具栏按钮**。 有关如何执行此操作的信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>添加到解决方案资源管理器工具栏按钮  
 本部分演练演示如何向其中添加按钮**解决方案资源管理器**工具栏。 单击该按钮，运行在该回调方法的代码。  
  
1.  在 ToolbarButtonPackage.vsct 文件中，转到`<Symbols>`部分。 `<GuidSymbol>`节点包含菜单组和包模板已生成命令。 添加`<IDSymbol>`到此节点，以声明的组，将保存您的命令的元素。  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  在`<Groups>`部分中，在现有的组条目后, 您声明的新组中定义上一步。  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     父级 GUID:ID 对设置为`guidSHLMainMenu`和`IDM_VS_TOOL_PROJWIN`放入此组**解决方案资源管理器**工具栏上，并在设置高优先级值将其放在其他命令组的后面。  
  
3.  在`<Buttons>`部分中，更改所生成的父 ID`<Button>`条目以反映您在上一步中定义的组。 已修改`<Button>`元素应如下所示︰  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  生成项目并启动调试。 将显示的实验实例。  
  
     **解决方案资源管理器**工具栏应显示现有的按钮右侧的新建命令按钮。 该按钮的图标是删除线。  
  
5.  单击新建按钮。  
  
     包含消息的对话框**ToolbarButtonPackage 内 SolutionToolbar.ToolbarButton.MenuItemCallback()**应显示。  
  
## <a name="controlling-the-visibility-of-a-button"></a>控制按钮的可见性  
 本部分演练演示如何控制工具栏按钮的可见性。 通过将上下文设置为中的一个或多个项目`<VisibilityConstraints>`部分 SolutionToolbar.vsct 文件的限制按钮以显示只有当项目均为打开。  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>若要打开一个或多个项目时显示的按钮  
  
1.  在`<Buttons>`部分的 ToolbarButtonPackage.vsct，将两个命令标志添加到现有`<Button>`元素、 之间`<Strings>`和`<Icons>`标记。  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible`和`DynamicVisibility`标志必须设置操作中的该条目`<VisibilityConstraints>`部分才会生效。  
  
2.  创建`<VisibilityConstraints>`具有两个部分`<VisibilityItem>`条目。 将这个新部分放在结束后立即`</Commands>`标记。  
  
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
  
     可见性的每一项表示在其下显示指定按钮的条件。 若要应用多个条件，必须创建多个条目为相同的按钮。  
  
3.  生成项目并启动调试。 将显示的实验实例。  
  
     **解决方案资源管理器**工具栏不包含删除线按钮。  
  
4.  打开包含项目的任何解决方案。  
  
     删除线按钮将出现在现有按钮右侧的工具栏。  
  
5.  在**文件**菜单上，单击**关闭解决方案**。 从工具栏中，该按钮即消失。  
  
 由控制按钮的可见性[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]直到加载 VSPackage。 加载 VSPackage 中之后，由 VSPackage 控制按钮的可见性。  有关详细信息，请参阅[MenuCommands Vs。OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)。  
  
## <a name="see-also"></a>另请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
