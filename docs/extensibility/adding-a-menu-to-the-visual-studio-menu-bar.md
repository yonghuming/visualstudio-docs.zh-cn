---
title: "添加到 Visual Studio 菜单栏的菜单 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "创建顶级菜单"
  - "顶级菜单"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 51
---
# 添加到 Visual Studio 菜单栏的菜单
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练演示如何向 Visual Studio 集成的开发环境 \(IDE\) 的菜单栏中添加一个菜单。 IDE 菜单栏包含菜单类别如 **文件**, ，**编辑**, ，**视图**, ，**窗口**, ，和 **帮助**。  
  
 在将一个新的菜单添加到 Visual Studio 菜单栏中之前, 请考虑您的命令是否应该放在现有菜单。 命令放置的详细信息，请参阅 [菜单和 Visual studio 命令](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。  
  
 菜单在.vsct 文件的项目中声明。 有关菜单和.vsct 文件的详细信息，请参阅 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 通过完成本演练，您可以创建一个名为菜单 **TestMenu** ，其中包含一条命令。  
  
## 系统必备  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 创建一个具有自定义命令项模板的 VSIX 项目  
  
1.  创建一个名为的 VSIX 项目 `TopLevelMenu`。 您可以找到中的 VSIX 项目模板 **新项目** 下的对话框 **Visual C\#** \/ **扩展性**。  有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  当项目打开后时，添加一个名为的自定义命令项模板 **TestCommand**。 在 **解决方案资源管理器**, ，用鼠标右键单击项目节点并选择 **添加 \/ 新项**。 在 **添加新项** 对话框中，转到 **Visual C\# \/ 可扩展性** ，然后选择 **自定义命令**。 在 **名称** 在窗口的底部字段中，命令文件名称更改为 **TestCommand.cs**。  
  
## 在 IDE 的菜单栏上创建菜单  
  
#### 若要创建菜单  
  
1.  在 **解决方案资源管理器**, ，打开 TestCommandPackage.vsct。  
  
     在文件末尾，是一个包含多个 \< GuidSymbol \> 节点的 \< 符号 \> 节点。 在名为 guidTestCommandPackageCmdSet 节点中，添加一个新的符号，如下所示︰  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  在 \< 命令 \> 节点中，就在 \< 组 \> 之前创建一个空的 \< 菜单 \> 节点。 在 \< 菜单 \> 节点将添加 \< 菜单 \> 节点，，如下所示︰  
  
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
  
     `guid` 和 `id` 指定的值菜单命令集和特定菜单中的命令集。  
  
     `guid` 和 `id` 父级值定位部分包含的工具和外接程序菜单的 Visual Studio 菜单栏上的菜单。  
  
     值 `CommandName` 字符串指定的文本应出现在菜单项。  
  
3.  \< 组 \> 部分中，找到 \< 组 \> 和 \< 父 \> 元素以指向我们刚添加的菜单更改︰  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     这样，新建菜单的组部分。  
  
4.  查找 `Buttons` 部分。 请注意， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 包模板已生成 `Button` 元素，将其设置为其父级 `MyMenuGroup`。 因此，此命令将显示在您的菜单。  
  
## 生成和测试扩展  
  
1.  生成项目并启动调试。 应显示的实验实例的实例。  
  
2.  菜单栏的实验实例中应包含 **TestMenu** 菜单。  
  
3.  在 **TestMenu** 菜单上，单击 **调用测试命令**。  
  
     一个消息框应该显示，并显示消息"第包内 TopLevelMenu.TestCommand.MenuItemCallback\(\) TestCommand"。 这表明，新的命令才起作用。  
  
## 请参阅  
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)