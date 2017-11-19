---
title: "将工具栏添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da6ea8eac18151f0efbaefb3e9f910b695630669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-toolbar"></a>添加工具栏
本演练演示如何将工具栏添加到 Visual Studio IDE。  
  
 工具栏是一个包含绑定到命令的按钮的水平或垂直条。 具体取决于其实现中，在 IDE 中的工具栏可以重新定位、 停靠在主 IDE 窗口中的任何一侧或保持其他窗口的前面。  
  
 此外，用户可以将命令添加到工具栏或从中删除通过使用**自定义**对话框。 通常情况下，在 Vspackage 中的工具栏是用户可自定义的。 IDE 处理所有自定义项，并 VSPackage 响应命令。 VSPackage 不需要知道命令所在的位置以物理方式。  
  
 有关菜单的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>使用工具栏创建扩展  
 创建一个名为的 VSIX 项目`IDEToolbar`。 添加名为的菜单命令项模板**ToolbarTestCommand**。 有关如何执行此操作的信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>为 IDE 创建工具栏  
  
1.  在 ToolbarTestCommandPackage.vsct，查找符号部分。 在名为 guidToolbarTestCommandPackageCmdSet GuidSymbol 元素中，添加一个工具栏和一个工具栏组中，声明，如下所示。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  在命令部分的顶部，创建菜单部分。 将菜单元素添加到要定义您的工具栏上的菜单部分。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     工具栏不能嵌套如子菜单。 因此，无需分配父组。 此外，你无需设置优先级，因为用户可以移动工具栏。 通常，工具栏的初始放置定义以编程方式，但用户的后续更改将永久保存。  
  
3.  在[组](../extensibility/groups-element.md)部分中，则为现有组项后, 定义[组](../extensibility/group-element.md)元素以包含工具栏上的命令。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  请在工具栏上显示的按钮。 在按钮部分中，将到工具栏按钮中的父块。 生成的按钮块应如下所示：  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     默认情况下，如果工具栏不具有任何命令，则不会不显示。  
  
5.  生成项目并启动调试。 应显示的实验实例。  
  
6.  右键单击 Visual Studio 菜单栏，以获取工具栏的列表。 选择**测试工具栏**。  
  
7.  你现在应看到您的工具栏上，作为文件图标中查找右侧的图标。 当你单击图标时，你应看到显示一个消息框**ToolbarTestCommandPackage。内部 IDEToolbar.ToolbarTestCommand.MenuItemCallback()**。  
  
## <a name="see-also"></a>另请参阅  
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)