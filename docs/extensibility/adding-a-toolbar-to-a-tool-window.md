---
title: "将工具栏添加到工具窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b094a04a9d2e273418edaa7cc4bc2d36f89e9d29
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>将工具栏添加到工具窗口
本演练演示如何将工具栏添加到工具窗口。  
  
 工具栏是一个包含绑定到命令按钮的水平或垂直条。 工具窗口中工具栏的长度始终为相同的宽度或高度的工具窗口中，具体取决于工具栏停靠的位置。  
  
 与在 IDE 中的工具栏，不同工具窗口中的工具栏必须停靠并且无法转移或自定义。 VSPackage 在非代码中编写的如果工具栏可停靠在任何边缘上。  
  
 有关如何将工具栏添加的详细信息，请参阅[将工具栏添加](../extensibility/adding-a-toolbar.md)。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>创建工具窗口工具栏  
  
1.  创建一个名为的 VSIX 项目`TWToolbar`具有这两个菜单命令名为**TWTestCommand**和工具窗口名为**TestToolWindow**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)和[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。 你需要在添加工具窗口模板之前添加命令项模板。  
  
2.  在 TWTestCommandPackage.vsct，查找符号部分。 在名为 guidTWTestCommandPackageCmdSet GuidSymbol 节点声明一个工具栏和工具栏组，如下所示。  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  在顶部`Commands`部分中，创建`Menus`部分。 添加`Menu`元素可定义工具栏。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     工具栏不能嵌套如子菜单。 因此，无需指定一个父级。 此外，你无需设置优先级，因为用户可以移动工具栏。 通常，工具栏的初始放置定义以编程方式，但用户的后续更改将永久保存。  
  
4.  在组部分中，定义一个组以包含工具栏命令。  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  在按钮部分中，将更改现有的 Button 元素的父级为工具栏组以便将显示工具栏。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     默认情况下，如果工具栏不具有任何命令，则不会不显示。  
  
     由于到工具窗口不会自动添加新的工具栏，则必须显式添加工具栏。 下一节中将对此进行讨论。  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>将工具栏添加到工具窗口  
  
1.  TWTestCommandPackageGuids.cs 中添加以下行。  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  在 TestToolWindow.cs 添加以下 using 语句。  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  TestToolWindow 构造函数中添加以下行。  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>测试工具窗口中的工具栏  
  
1.  生成项目并启动调试。 应显示 Visual Studio 实验实例。  
  
2.  上**视图 / 其他窗口**菜单上，单击**测试工具窗口**以显示该工具窗口。  
  
     你应看到在顶部的工具栏 （它类似于默认图标） 左下的工具窗口标题的下方。  
  
3.  在工具栏上，单击图标以显示消息**TWTestCommandPackage 内 TWToolbar.TWTestCommand.MenuItemCallback()**。  
  
## <a name="see-also"></a>另请参阅  
 [添加工具栏](../extensibility/adding-a-toolbar.md)
