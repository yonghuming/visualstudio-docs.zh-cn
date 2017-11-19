---
title: "部署 Visual Studio 中的 SharePoint 工具扩展 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying extensions
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0145982781ca3e21229a7af46090ed2addcaccde
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>在 Visual Studio 中部署 SharePoint 工具扩展
  若要部署 SharePoint 工具扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包含扩展程序集，以及你想要随此扩展分发的任何其他文件的扩展 (VSIX) 包。 VSIX 包是一个压缩的文件，遵循开放式打包约定 (OPC) 标准。 VSIX 包具有.vsix 扩展名。  
  
 创建 VSIX 包后，其他用户可以运行要安装扩展的.vsix 文件。 当用户安装你的扩展时，所有文件将安装到 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 文件夹。 若要将扩展部署，你可以上载到 VSIX 包[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)网站，也可以将包分发给您的客户以某种其他方式，如宿主的网络共享或某些其他网站上的包。  
  
 有关创建 VSIX 包并将它们到部署的详细信息[Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)，请参阅[传送 Visual Studio 扩展](/visualstudio/extensibility/shipping-visual-studio-extensions)。  
  
 你可以通过创建 VSIX 包**VSIX 项目**模板 Visual Studio 中，或者您可以手动创建 VSIX 包。  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>使用 VSIX 项目创建 VSIX 包  
 你可以使用**VSIX 项目**提供 Visual Studio SDK 创建 VSIX 包，为 SharePoint 工具扩展的模板。 使用 VSIX 项目基础上手动创建 VSIX 包提供了以下几个好处：  
  
-   生成项目时，visual Studio 自动生成 VSIX 包。 为你完成任务，例如向包添加部署文件和创建包的 [Content_Types].xml 文件。  
  
-   你可以配置要 VSIX 包中包括你的扩展项目和其他文件，如项目模板和项模板的生成输出的 VSIX 项目。  
  
 有关使用 VSIX 项目的详细信息，请参阅[VSIX 项目模板](/visualstudio/extensibility/vsix-project-template)。  
  
### <a name="organizing-your-projects"></a>组织你的项目  
 默认情况下，VSIX 项目仅生成 VSIX 包，而非程序集。 因此，你通常也不实现 SharePoint 工具扩展的 VSIX 项目中。 你通常使用至少两个项目：  
  
-   一个 VSIX 项目。  
  
-   一个用于实现你的扩展的库项目。  
  
 您还可以使用与其他项目对于某些类型的扩展：  
  
-   一个用于实现你的扩展使用任何 SharePoint 命令的库项目。 有关演示此方案的演练，请参阅[演练： 扩展服务器资源管理器显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   如果你的扩展定义新的 SharePoint 项目项类型创建的项模板或项目模板中，一个项模板或项目模板项目。 有关演示此方案的演练，请参阅[演练： 使用项模板，第 1 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
-   一个用于实现的项模板或项目模板的自定义向导，如果你的扩展包含的模板的库项目。 有关演示此方案的演练，请参阅[演练： 使用项模板，第 2 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
 如果你在同一 Visual Studio 解决方案中包含的所有项目，你可以修改在 VSIX 项目以包括类库项目的生成输出 source.extension.vsixmanifest 文件。  
  
### <a name="editing-the-vsix-manifest"></a>编辑 VSIX 清单  
 你必须编辑 source.extension.vsixmanifest 文件中在 VSIX 项目，若要包括你想要包含在你扩展中的所有项的项。 当从其快捷菜单中打开 source.extension.vsixmanifest 文件中时，该文件将显示用于编辑 XML 文件中提供的用户界面的设计器中。 有关详细信息，请参阅[VSIX 清单设计器](/visualstudio/extensibility/vsix-manifest-designer)。  
  
 必须将条目添加到 source.extension.vsixmanifest 文件中对以下各项：  
  
-   扩展程序集。  
  
-   实现你的扩展使用任何 SharePoint 命令的程序集。  
  
-   任何项目模板或与你的扩展关联的项模板。  
  
-   与你的扩展关联的模板自定义向导。  
  
 下面的过程介绍如何将条目添加到的.vsixmanifest 文件中，为每个这些项。  
  
##### <a name="to-include-the-extension-assembly"></a>若要包括的扩展程序集  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**。  
  
     在设计器中打开该文件  
  
2.  上**资产**选项卡的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
4.  在**源**列表中，执行以下步骤之一：  
  
    -   如果扩展程序集，生成的项目是在 VSIX 项目的同一个解决方案中，选择**当前解决方案中的项目**。 在**项目**列表中，选择项目的名称。  
  
    -   如果为你的项目中的文件包括扩展程序集，则选择**在文件系统上的文件**。 在**路径**列表中，到扩展程序集文件中，输入完整路径或使用**浏览**按钮以找到并选择程序集文件。  
  
5.  选择“确定”  按钮。  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>包含 SharePoint 命令程序集  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**按钮。  
  
     在设计器中打开该文件。  
  
2.  在**资产**部分的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
3.  在**类型**框中，输入**SharePoint.Commands.v4**。  
  
4.  在**源**列表中，执行以下步骤之一：  
  
    -   如果命令程序集生成的项目是在 VSIX 项目的同一个解决方案中，选择**当前解决方案中的项目**。 在**项目**列表中，选择项目的名称。  
  
    -   如果为你的项目中的文件包括命令程序集，则选择**在文件系统上的文件**。 在**路径**列表中，到扩展程序集文件中，输入完整路径或使用**浏览**按钮以找到并选择程序集文件。  
  
5.  选择“确定”  按钮。  
  
##### <a name="to-include-a-template-that-you-create"></a>若要包括你创建的模板  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**按钮。  
  
     在设计器中打开该文件。  
  
2.  在**资产**部分的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
4.  在**源**列表中，选择**当前解决方案中的项目**。  
  
5.  在**项目**列表，选择该项目的名称，然后选择**确定**按钮。  
  
6.  在**解决方案资源管理器**，打开你的项目模板或项模板项目的快捷菜单，然后选择**卸载项目**。  
  
7.  同样，打开项目节点的快捷菜单，然后选择**编辑***YourTemplateProjectName***.csproj**或**编辑***YourTemplateProjectName***.vbproj**。  
  
8.  找到以下`VSTemplate`项目文件中的元素。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. 用下列 XML 替换此元素。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`元素指定其他文件夹中生成项目时在其下创建的项目模板的路径。 此处指定的文件夹确保仅在客户打开时，将导致项模板可用**添加新项目**对话框框中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
10. 保存并关闭文件。  
  
11. 在**解决方案资源管理器**，打开项目模板或项模板项目的快捷菜单，然后选择**重新加载项目**。  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>若要包括手动创建的模板  
  
1.  在 VSIX 项目中，将添加到项目后，要包含模板的新文件夹。  
  
2.  在此新文件夹中，创建以下子文件夹，然后将模板 (.zip) 文件添加到*区域设置 ID*文件夹。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *区域设置 ID*  
  
     *YourTemplateName*.zip  
  
     例如，如果你有一个名为 ContosoCustomAction.zip 支持英语 （美国） 区域设置的项模板，则完整的路径可能 ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip。  
  
3.  在**解决方案资源管理器**，选择的模板文件 (*YourTemplateName*.zip)。  
  
4.  在**属性**窗口中，设置**生成操作**属性**内容**。  
  
5.  打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**。  
  
     在设计器中打开该文件。  
  
6.  在**资产**部分的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
7.  在**类型**列表中，选择**Microsoft.VisualStudio.ItemTemplate**或**Microsoft.VisualStudio.ProjectTemplate**。  
  
8.  在**源**列表中，选择**在文件系统上的文件**。  
  
9. 在**路径**字段中，输入程序集的完整路径 (例如， **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**，或使用**浏览**按钮来定位并选择该程序集，，然后选择**确定**按钮。  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>若要包括项目模板或项模板的向导  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**。  
  
     在设计器中打开该文件。  
  
2.  在**资产**部分的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
3.  在**类型**列表中，选择**Microsoft.VisualStudio.Assembly**。  
  
4.  在**源**列表中，执行以下步骤之一：  
  
    -   如果向导程序集生成的项目是在 VSIX 项目的同一个解决方案中，选择**当前解决方案中的项目**。 在**项目**列表中，选择项目的名称。  
  
    -   如果为你的项目中的文件包括向导程序集，则选择**在文件系统上的文件**。 在**路径**字段中，输入程序集文件中，完整路径或使用**浏览**按钮以找到并选择该程序集。  
  
5.  选择“确定”  按钮。  
  
### <a name="related-walkthroughs"></a>相关的演练  
 下表列出的演练，演示如何使用 VSIX 项目来部署不同类型的 SharePoint 工具扩展。  
  
|扩展类型|相关的演练|  
|--------------------|--------------------------|  
|包括的扩展程序集扩展|[演练：扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [演练：创建 SharePoint 项目扩展](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [演练：在服务器资源管理器扩展中调入 SharePoint 客户端对象模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|一个扩展，包括 SharePoint 命令|[演练：为 SharePoint 项目创建自定义部署步骤](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [演练：扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [演练：使用项目模板创建站点栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|一个扩展，包括 Visual Studio 模板|[演练：使用项模板创建自定义操作项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [演练：使用项目模板创建站点栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|包括模板向导扩展|[演练：使用项模板创建自定义操作项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [演练：使用项目模板创建站点栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>手动创建 VSIX 包  
 如果你想要手动创建你的 SharePoint 工具扩展的 VSIX 包，请执行以下步骤：  
  
1.  在新的文件夹中创建 extension.vsixmanifest 文件和 [Content_Types].xml 文件。 有关详细信息，请参阅[剖析 VSIX 包](/visualstudio/extensibility/anatomy-of-a-vsix-package)。  
  
2.  在 Windows 资源管理器，右键单击包含两个 XML 文件的文件夹，单击发送到，然后单击压缩 (zipped) 文件夹。 将生成的.zip 文件重命名为 Filename.vsix，这里的文件名是安装你的包的可再发行文件的名称。  
  
3.  将扩展程序集添加到 VSIX 包。 如果你的扩展包括 SharePoint 命令，还添加实现了 SharePoint 命令的 VSIX 包的程序集。  
  
4.  修改 extension.vsixmanifest 文件：  
  
    -   添加`Microsoft.VisualStudio.MefComponent`元素下的`Assets`元素，，然后将设置为实现你的扩展的 VSIX 包中的程序集的相对路径的新元素的值。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
    -   如果你的扩展包括 SharePoint 命令用于为 SharePoint 中调入服务器对象模型，添加`Microsoft.VisualStudio.Assembly`元素下的`Assets`元素。 将新元素的值设置为 VSIX 包中实现 SharePoint 命令的程序集的相对路径。 有关详细信息，请参阅[资产元素 （VSX 架构）](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
    -   如果你的扩展包括项目模板或项模板，可添加`ProjectTemplate`或`ItemTemplate`元素下的`Assets`元素。 将新元素的值设置为包含 VSIX 包中的模板的文件夹的相对路径。 有关详细信息，请参阅[ProjectTemplate 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)和[ItemTemplate 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
    -   如果你的扩展包括项目模板或项模板的自定义向导，将添加`Assembly`元素下的`Assets`元素。 将新元素的值设置为 VSIX 包中的程序集的相对路径，然后设置`AssemblyName`属性设为完整的程序集名称 （包括版本、 区域性和公钥标记）。 有关详细信息，请参阅[依赖关系元素 （VSX 架构）](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37)。  
  
### <a name="example"></a>示例  
 下面的示例演示 SharePoint 工具扩展 extension.vsixmanifest 文件的内容。 扩展是在名为 Contoso.ProjectExtension.dll 程序集中实现的。 扩展包括 SharePoint 命令程序集 Contoso.ExtensionCommands.dll 和项模板名为的文件夹下名为**ItemTemplates** VSIX 包中。 此示例假定这两个程序集位于 VSIX 包中的 extension.vsixmanifest 文件所在的文件夹。  
  
```  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)   
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [在 Visual Studio 中调试 SharePoint 工具扩展](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  