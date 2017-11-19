---
title: "将菜单添加到 Visual Studio 菜单栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: "51"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e4a2485b7e702844a037787234ef3a1ab66495d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>将菜单添加到 Visual Studio 菜单栏
本演练演示如何向 Visual Studio 集成的开发环境 (IDE) 的菜单栏添加菜单。 IDE 菜单栏包含菜单类别如**文件**，**编辑**，**视图**，**窗口**，和**帮助**.  
  
 在将新菜单添加到 Visual Studio 菜单栏中之前, 请考虑你的命令是否应放置在现有菜单内。 命令放置有关的详细信息，请参阅[菜单和命令 for Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。  
  
 菜单项目的.vsct 文件中声明。 有关菜单和.vsct 文件的详细信息，请参阅[命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 通过完成本演练，你可以创建一个名为菜单**TestMenu**包含一个命令。  
  
## <a name="prerequisites"></a>先决条件  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>创建一个具有自定义命令项模板的 VSIX 项目  
  
1.  创建一个名为的 VSIX 项目`TopLevelMenu`。 你可以查找中的 VSIX 项目模板**新项目**下的对话框**Visual C#** / **扩展性**。  有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  在项目打开，添加名为的自定义命令项模板**TestCommand**。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**TestCommand.cs**。  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>在 IDE 的菜单栏上创建菜单  
  
#### <a name="to-create-a-menu"></a>创建菜单  
  
1.  在**解决方案资源管理器**，打开 TestCommandPackage.vsct。  
  
     在文件末尾，没有\<符号 > 节点，其中包含几个\<GuidSymbol > 节点。 在名为 guidTestCommandPackageCmdSet 节点中，添加一个新的符号，，如下所示：  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  创建一个空\<菜单 > 中的节点\<命令 > 节点，之前\<组 >。 在\<菜单 > 节点，添加\<菜单 > 节点，如下所示：  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     `guid`和`id`菜单的值指定命令集和特定菜单中的命令集。  
  
     `guid`和`id`的父值的 Visual Studio 菜单栏包含工具和外接程序菜单部分定位菜单。  
  
     值`CommandName`字符串指定的文本应出现在菜单项。  
  
3.  在\<组 > 部分中，找到\<组 > 并将更改\<父 > 元素以指向我们刚添加的菜单：  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     这使得新菜单的组部分。  
  
4.  查找`Buttons`部分。 请注意，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]生成包模板`Button`已设置为其父级的元素`MyMenuGroup`。 因此，此命令将显示在你的菜单。  
  
## <a name="building-and-testing-the-extension"></a>生成和测试扩展  
  
1.  生成项目并启动调试。 应显示的实验实例的实例。  
  
2.  在实验实例中的菜单栏应包含**TestMenu**菜单。  
  
3.  上**TestMenu**菜单上，单击**调用测试命令**。  
  
     一个消息框应该显示，并显示消息"第包内 TopLevelMenu.TestCommand.MenuItemCallback() TestCommand"。 这表示该新命令起作用。  
  
## <a name="see-also"></a>另请参阅  
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)