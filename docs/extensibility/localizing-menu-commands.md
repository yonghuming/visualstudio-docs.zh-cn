---
title: "本地化菜单命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 586f087e4c0cbd087bd06d7dc54a524b09ae21c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-menu-commands"></a>本地化菜单命令
你可以提供本地化的文本的菜单和工具栏通过创建本地化的.vsct 文件的命令和本地化以及你的 VSPackage，然后更新项目文件的更改合并的.resx 文件。  
  
 有关如何本地化安装体验的信息，请参阅[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="localizing-command-names"></a>本地化的命令名称  
 在 Vspackage 中，在.vsct 文件中定义是菜单命令和工具栏按钮。  
  
1.  在**解决方案资源管理器**，更改中的.vsct 文件的名称*filename*到.vsct *filename*.en US.vsct。  
  
2.  制作的副本*filename*.en-US.vsct 每个本地化语言。  
  
     将每个副本*filename*。*区域设置*.vsct，其中*区域设置*是特定区域性名称。 区域性名称值的列表，请参阅[由 Microsoft 分配的区域设置 Id](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx)。  
  
     这些*filename*。*区域设置*.vsct 文件将包含你的包的本地化的菜单文本。  
  
3.  打开每个*filename*。*区域设置*.vsct 文件的文本进行本地化。  
  
    1.  修改[ButtonText](../extensibility/buttontext-element.md)元素值以适合特定的语言。  
  
    2.  如果你将提供本地化的图标，修改[位图](../extensibility/bitmap-element.md)值指向的目标文件。  
  
     下面的示例演示命令，以打开系列树资源管理器工具窗口的英语和西班牙语按钮文本。  
  
     [FamilyTree.en US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>本地化文本中的其他资源  
 资源 (.resx) 文件中定义了文本资源而不是命令名称。  
  
1.  将 VSPackage.resx 重命名为 VSPackage.en US.resx。  
  
2.  请为每种本地化语言 VSPackage.en US.resx 文件的副本。  
  
     将每个副本 VSPackage。*区域设置*.resx，其中*区域设置*是特定区域性名称。  
  
3.  将 Resources.resx 重命名为 Resources.en US.resx。  
  
4.  请为每种本地化语言 Resources.en US.resx 文件的副本。  
  
     将每个副本的资源。*区域设置*.resx，其中*区域设置*是特定区域性名称。  
  
5.  打开每个.resx 文件中以修改作为适用于特定语言和区域性的字符串值。 下面的示例显示一个工具窗口的标题栏的本地化的资源定义。  
  
     [Resources.en US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>将本地化的资源合并到项目  
 你必须修改 assemblyinfo.cs 文件和项目文件以合并的本地化的资源。  
  
1.  从**属性**中的节点**解决方案资源管理器**，在编辑器中打开 assemblyinfo.cs 或 assemblyinfo.vb。  
  
2.  添加以下一项。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     这将设置美国英语为默认语言。  
  
3.  卸载项目。  
  
4.  在编辑器中打开项目文件。  
  
5.  找到`ItemGroup`包含的元素`EmbeddedResource`元素。  
  
6.  在`EmbeddedResource`调用 VSPackage.en US.resx 的元素替换`ManifestResourceName`具有元素`LogicalName`元素，设置为`VSPackage.en-US.Resources`、，如下所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  对于每种本地化语言复制`EmbeddedResource`VsPackage.en 美国并设置的元素**包括**属性和**LogicalName**元素复制到目标区域设置，如以下所示示例。  
  
8.  给每个本地化`VSCTCompile`元素中，添加`ResourceName`指向的元素`Menus.ctmenu`，下面的示例中所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. 保存项目文件并重新加载项目。  
  
10. 生成项目。  
  
     这将创建一个主要的程序集，并为每种语言的资源程序集。 本地化的部署过程的信息，请参阅[本地化 VSIX 包](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>另请参阅  
 [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands 与OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)