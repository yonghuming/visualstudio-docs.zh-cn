---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  若要部署 SharePoint 工具扩展，请创建一个包含要随此扩展分发的扩展程序集和任何其他文件的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包。  VSIX 包是一个遵循开放式打包约定 \(OPC\) 标准的压缩文件。  VSIX 包的扩展名为 .vsix。  
  
 创建 VSIX 包之后，其他用户可以运行 .vsix 文件安装您的扩展。  当用户安装您的扩展时，所有文件都会安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions 文件夹。  若要部署扩展，可将 VSIX 包上载到 [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847)（Visual Studio 库）网站，也可以通过其他方法将该包分发给客户（如在网络共享或其他一些网站上承载该包）。  
  
 有关创建 VSIX 包和将其部署到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847)的更多信息，请参见[传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)。  
  
 可以使用 Visual Studio 中的**“VSIX 项目”**模板创建 VSIX 包，也可以手动创建 VSIX 包。  
  
## 使用 VSIX 项目创建 VSIX 包  
 可以使用 Visual Studio SDK 提供的**“VSIX 项目”**模板为 SharePoint 工具扩展创建 VSIX 包。  与手动创建 VSIX 包相比，使用 VSIX 项目有以下几个好处：  
  
-   当您生成项目时，Visual Studio 会自动生成 VSIX 包。  并为您完成向包中添加部署文件和为包创建 \[Content\_Types\].xml 文件等任务。  
  
-   可以将 VSIX 项目配置为将扩展项目的生成输出和其他文件（例如，项目模板和项模板）包含在 VSIX 包中。  
  
 有关使用 VSIX 项目的更多信息，请参见[VSIX 项目模板](../extensibility/vsix-project-template.md)。  
  
### 组织项目  
 默认情况下，VSIX 项目只生成 VSIX 包而非程序集。  因此，您通常不会在 VSIX 项目中实现 SharePoint 工具扩展。  一般来说，您至少会使用两个项目：  
  
-   一个 VSIX 项目。  
  
-   一个实现扩展的类库项目。  
  
 您还可以使用特定类型的扩展的其他项目：  
  
-   一个实现扩展使用的任何 SharePoint 命令的类库项目。  有关演示此方案的演练，请参见[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   一个用于创建项模板或项目模板的项模板项目或项目模板项目（如果扩展定义了 SharePoint 项目项的新类型）。  有关演示此方案的演练，请参见[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
-   一个为项模板或项目模板实现自定义向导的类库项目（如果扩展包含一个模板）。  有关演示此方案的演练，请参见[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
 如果同一个 Visual Studio 解决方案中包括所有项目，则可修改 VSIX 项目中的 source.extension.vsixmanifest 文件，以包括类库项目的生成输出。  
  
### 编辑 VSIX 清单  
 您必须在 VSIX 项目中编辑 source.extension.vsixmanifest 文件，以包括要包含在扩展中的所有项的条目。  当您打开从其快捷菜单中的 source.extension.vsixmanifest 文件，该文件将出现在编辑文件中的 XML 提供一个用户界面的设计器。  有关更多信息，请参见[VSIX 清单设计器](../extensibility/media/vsix-manifest-designer.png)。  
  
 必须在 source.extension.vsixmanifest 文件中添加针对以下项的条目：  
  
-   扩展程序集。  
  
-   用于实现扩展使用的任何 SharePoint 命令的程序集。  
  
-   与扩展关联的任何项目模板或项模板。  
  
-   与扩展关联的模板的自定义向导。  
  
 以下过程介绍如何在 .vsixmanifest 文件中添加针对以下每个项的条目。  
  
##### 包括扩展程序集  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开**。  
  
     在设计器中打开文件。  
  
2.  在编辑器中 **资产** 选项卡中，选择 **新建** 按钮。  
  
     **添加新资产** 对话框打开。  
  
3.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
4.  在 **源** 列表中，执行以下步骤之一：  
  
    -   如果扩展程序集从与 VSIX 项目处于同一解决方案，选择 **当前解决方案中的项目**的项目随即生成。  在 **项目** 列表中，选择该项的名称。  
  
    -   如果扩展程序集包含，当在项目的文件，选择 **在文件系统中的文件**。  在 **路径** 列表，输入完整路径。扩展程序集文件或使用 **浏览** 按钮查找并选择该程序集文件。  
  
5.  选择**“确定”**按钮。  
  
##### 包括 SharePoint 命令程序集  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开** 按钮。  
  
     文件即会在设计器中打开。  
  
2.  在编辑器中 **资产** 部分中，选择 **新建** 按钮。  
  
     **添加新资产** 对话框打开。  
  
3.  在 **类型** 框中，输入 **SharePoint.Commands.v4**。  
  
4.  在 **源** 列表中，执行以下步骤之一：  
  
    -   如果命令程序集从与 VSIX 项目处于同一解决方案，选择 **当前解决方案中的项目**的项目随即生成。  在 **项目** 列表中，选择该项的名称。  
  
    -   如果命令程序集包含，当在项目的文件，选择 **在文件系统中的文件**。  在 **路径** 列表，输入完整路径。扩展程序集文件或使用 **浏览** 按钮查找并选择该程序集文件。  
  
5.  选择**“确定”**按钮。  
  
##### 包含创建的模板  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开** 按钮。  
  
     文件即会在设计器中打开。  
  
2.  在编辑器中 **资产** 部分中，选择 **新建** 按钮。  
  
     **添加新资产** 对话框打开。  
  
3.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.ProjectTemplate** 或 **Microsoft.VisualStudio.ItemTemplate**。  
  
4.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
5.  在 **项目** 列表中，选择项目的名称，然后选择 **确定** 按钮。  
  
6.  在 **解决方案资源管理器**，请打开项目模板或项模板项目的快捷菜单，然后选择 **卸载项目**。  
  
7.  再次打开项目节点的快捷菜单，然后选择 **编辑***YourTemplateProjectName***.csproj** 或 **编辑***YourTemplateProjectName***.vbproj**。  
  
8.  定位到项目文件中的以下 `VSTemplate` 元素。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. 用以下 XML 替换此元素。  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 元素指定路径中的其他文件夹，在生成项目时将在这些文件夹中创建项目模板。  此处指定的文件夹可确保项模板仅可用，仅当客户打开 **添加新项目** 对话框时，展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
10. 保存并关闭文件。  
  
11. 在 **解决方案资源管理器**，请打开项目模板或项模板项目的快捷菜单，然后选择 **重新加载项目**。  
  
##### 包含手动创建的模板  
  
1.  在 VSIX 项目中，向项目中添加一个用于包含模板的新文件夹。  
  
2.  在此新文件夹下，创建以下子文件夹，然后将模板 \(.zip\) 文件添加到*区域设置 ID* 文件夹。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Locale ID*  
  
     *YourTemplateName*.zip  
  
     例如，如果有一个名为 ContosoCustomAction.zip 的项模板，并且该模板支持英语（美国）区域设置，则完整路径可能为 ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip。  
  
3.  在 **解决方案资源管理器**，选择模板文件 \(*YourTemplateName*.zip\)。  
  
4.  在**“属性”**窗口中，将**“生成操作”**属性设置为**“内容”**。  
  
5.  打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开**。  
  
     文件即会在设计器中打开。  
  
6.  在编辑器中 **资产** 部分中，选择 **新建** 按钮。  
  
     **添加新资产** 对话框打开。  
  
7.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.ItemTemplate** 或 **Microsoft.VisualStudio.ProjectTemplate**。  
  
8.  在 **源** 列表中，选择 **在文件系统中的文件**。  
  
9. 在 **路径** 字段中，输入完整路径到程序集 \(例如，**ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip**或使用 **浏览** 按钮查找并选择该程序集，然后选择 **确定** 按钮。  
  
##### 包含项目模板或项模板的向导  
  
1.  在 VSIX 项目中，打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开**。  
  
     文件即会在设计器中打开。  
  
2.  在编辑器中 **资产** 部分中，选择 **新建** 按钮。  
  
     **添加新资产** 对话框打开。  
  
3.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.Assembly**。  
  
4.  在 **源** 列表中，执行以下步骤之一：  
  
    -   如果向导程序集从与 VSIX 项目处于同一解决方案，选择 **当前解决方案中的项目**的项目随即生成。  在 **项目** 列表中，选择该项的名称。  
  
    -   如果向导程序集，包括在您的项目中的文件，选择 **在文件系统中的文件**。  在 **路径** 字段中，输入完整路径为程序集文件或使用 **浏览** 按钮查找并选择该程序集。  
  
5.  选择**“确定”**按钮。  
  
### 相关演练  
 下表列出了一些演练，这些演练演示如何使用 VSIX 项目部署不同类型的 SharePoint 工具扩展。  
  
|扩展类型|相关演练|  
|----------|----------|  
|只包含扩展程序集的扩展|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|包含 SharePoint 命令的扩展|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|包含 Visual Studio 模板的扩展|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|包含模板向导的扩展|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## 手动创建 VSIX 包  
 如果要为 SharePoint 工具扩展手动创建 VSIX 包，请执行以下步骤：  
  
1.  创建 extension.vsixmanifest 文件、\[Content\_Types\].xml 和 VSIX 包文件（.vsix 文件）。  有关更多信息，请参见[VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)和[如何：手动将扩展打包（VSIX 部署）](~/misc/how-to-manually-package-an-extension-vsix-deployment.md)。  
  
2.  将扩展程序集添加到 VSIX 包中。  如果扩展中包括某个 SharePoint 命令，则也将实现该 SharePoint 命令的程序集添加到 VSIX 包中。  
  
3.  修改 extension.vsixmanifest 文件：  
  
    -   添加一个 `Microsoft.VisualStudio.MefComponent` 元素在 `Assets` 元素的下方，然后将新元素的值设置为实现 VSIX 包中的扩展程序集的相对路径。  有关更多信息，请参见[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
    -   如果扩展中包括调入 SharePoint 的服务器对象模型的 SharePoint 命令，添加一个 `Microsoft.VisualStudio.Assembly` 元素在 `Assets` 元素下。  将新元素的值设置为实现 VSIX 包中的 SharePoint 命令的程序集的相对路径。  有关更多信息，请参见[属性元素 \(VSX 架构\)](http://msdn.microsoft.com/zh-cn/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
    -   如果扩展包含项目模板或项模板，添加一个 `ProjectTemplate` 或 `ItemTemplate` 元素在 `Assets` 元素下。  将新元素的值设置为包含 VSIX 包模板文件夹的相对路径。  有关更多信息，请参见[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/87add64c-9dcd-495f-8815-209dab182cb1)和[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
    -   如果扩展包含项目模板或项模板的自定义向导中，添加一个 `Assembly` 元素在 `Assets` 元素下。  将新元素的值到程序集的相对路径在 VSIX 包中，然后将 `AssemblyName` 属性设置为完整程序集名称 \(包括版本、区域性和公钥标记\)。  有关更多信息，请参见[依赖项元素 \(VSX 架构\)](http://msdn.microsoft.com/zh-cn/1f63f60a-98ad-48ec-8e44-4eba383d3e37)。  
  
### 示例  
 下面的示例演示 SharePoint 工具扩展的 extension.vsixmanifest 文件的内容。  该扩展在授予 Contoso.ProjectExtension.dll 的程序集中实现。  该扩展包含授予 Contoso.ExtensionCommands.dll 和项模板在文件夹下在 VSIX 包名为 **ItemTemplates** 的 SharePoint 命令程序集。  此示例假定这两个程序集都与 VSIX 包中的 extension.vsixmanifest 文件位于同一文件夹中。  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
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
  
## 请参阅  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  