---
title: "演练： 使用项目模板创建网站栏项目项，第 1 部分 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1033f33835dfdeefbb4791e356ca50a577b789ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1"></a>演练：使用项目模板创建网站栏项目项（第 1 部分）
  SharePoint 项目是一个或多个 SharePoint 项目项的容器。 可以通过创建你自己的 SharePoint 项目项类型，然后将其关联的项目模板来扩展 Visual Studio 中的 SharePoint 项目系统。 在此演练中，将为创建网站栏，定义项目项类型，然后你将在其中创建可用来创建一个包含网站栏项目项的新项目的项目模板。  
  
 本演练演示了下列任务：  
  
-   创建一个 Visual Studio 扩展定义一种新网站栏的 SharePoint 项目项。 项目项类型都包含一个简单的自定义属性，将出现在**属性**窗口。  
  
-   创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]项目项的项目模板。  
  
-   生成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包来部署项目模板和扩展程序集。  
  
-   调试和测试项目项。  
  
 这是一个独立的演练。 完成本演练后，你可以通过将向导添加到项目模板来增强项目项。 有关详细信息，请参阅[演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
> [!NOTE]  
>  你可以下载包含已完成的项目、 代码和从以下位置在本演练中的其他文件的示例： [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练的开发计算机上：  
  
-   支持的版本的 Microsoft Windows 中，SharePoint 和[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本演练使用**VSIX 项目**SDK 创建 VSIX 包来部署项目项中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   在 SharePoint 中的网站栏。 有关详细信息，请参阅[列](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
-   Visual Studio 中的项目模板。 有关详细信息，请参阅[创建项目和项模板](/visualstudio/ide/creating-project-and-item-templates)。  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，你需要创建三个项目：  
  
-   一个 VSIX 项目。 此项目创建 VSIX 包来部署网站栏项目项和项目模板。  
  
-   一个项目模板项目。 此项目创建可用来创建一个包含网站栏项目项的新 SharePoint 项目的项目模板。  
  
-   一个类库项目。 此实现定义的网站栏项目项的行为的 Visual Studio 扩展的项目。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-vsix-project"></a>若要创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  在顶部**新项目**对话框框中，请确保**.NET Framework 4.5**选择在列表中的.NET framework 的版本。  
  
4.  展开**Visual Basic**或**Visual C#**节点，然后选择**扩展性**节点。  
  
    > [!NOTE]  
    >  **扩展性**节点是安装 Visual Studio SDK 时才可用。 有关详细信息，请参阅本主题前面的先决条件部分。  
  
5.  在项目模板列表中，选择**VSIX 项目**。  
  
6.  在**名称**框中，输入**SiteColumnProjectItem**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**SiteColumnProjectItem**项目合并为**解决方案资源管理器**。  
  
#### <a name="to-create-the-project-template-project"></a>若要创建项目模板项目  
  
1.  在**解决方案资源管理器**，打开解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在顶部**新项目**对话框框中，请确保**.NET Framework 4.5**选择在列表中的.NET framework 的版本。  
  
3.  展开**Visual C#**或**Visual Basic**节点，然后选择**扩展性**节点。  
  
4.  在项目模板列表中，选择**C# 项目模板**或**Visual Basic 项目模板**模板。  
  
5.  在**名称**框中，输入**SiteColumnProjectTemplate**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**SiteColumnProjectTemplate**到解决方案的项目。  
  
6.  从项目中删除 Class1 代码文件。  
  
7.  如果你创建 Visual Basic 项目，还从项目中删除以下文件：  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>若要创建扩展项目  
  
1.  在**解决方案资源管理器**，打开解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在顶部**新项目**对话框框中，请确保**.NET Framework 4.5**选择在列表中的.NET framework 的版本。  
  
3.  展开**Visual C#**或**Visual Basic**节点，选择**Windows**节点，然后选择**类库**模板。  
  
4.  在**名称**框中，输入**ProjectItemTypeDefinition** ，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**ProjectItemTypeDefinition**到解决方案的项目并打开默认 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-extension-project"></a>配置扩展项目  
 添加代码文件和程序集引用，来配置扩展项目。  
  
#### <a name="to-configure-the-project"></a>若要配置项目  
  
1.  在 ProjectItemTypeDefinition 项目中，添加名为的代码文件**SiteColumnProjectItemTypeProvider**。  
  
2.  在菜单栏上，依次选择“项目”、“添加引用”。  
  
3.  在**引用管理器-ProjectItemTypeDefinition**对话框框中，展开**程序集**节点，选择**Framework**节点，，然后选择System.ComponentModel.Composition 复选框。  
  
4.  选择**扩展**节点，选择 Microsoft.VisualStudio.SharePoint 程序集，旁边的复选框，然后选择**确定**按钮。  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>将新的 SharePoint 项目项类型定义  
 创建一个类以实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>接口可定义新的项目项类型的行为。 无论何时你想要定义新类型的项目项，则实现此接口。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定义新的 SharePoint 项目项类型  
  
1.  在**SiteColumnProjectItemTypeProvider**代码文件，将默认代码替换为以下代码，然后保存该文件。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="creating-a-visual-studio-project-template"></a>创建 Visual Studio 项目模板  
 通过创建项目模板，你可以启用其他开发人员可以创建包含站点列项目项的 SharePoint 项目。 SharePoint 项目模板包括所需的所有项目在 Visual Studio 中，如.csproj 或.vbproj 和.vstemplate 文件，以及特定于 SharePoint 项目的文件的文件。 有关详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 在此过程中，你将创建一个空的 SharePoint 项目，以生成特定于 SharePoint 项目的文件。 你将这些文件到 SiteColumnProjectTemplate 项目以便其包含在此项目中生成的模板。 你还配置 SiteColumnProjectTemplate 项目文件，以指定项目模板中的显示位置**新项目**对话框。  
  
#### <a name="to-create-the-files-for-the-project-template"></a>若要创建项目模板的文件  
  
1.  启动第二个实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有管理凭据。  
  
2.  创建名为的 SharePoint 2010 项目**BaseSharePointProject**。  
  
    > [!IMPORTANT]  
    >  在**SharePoint 自定义向导**，不要选择**部署为场解决方案**选项按钮。  
  
3.  将空元素项添加到项目中，并将其命名为项**Field1**。  
  
4.  保存该项目，然后关闭第二个实例[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
5.  实例中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在其 SiteColumnProjectItem 解决方案打开、**解决方案资源管理器**，打开快捷菜单**SiteColumnProjectTemplate**项目节点，选择**添加**，然后选择**现有项**。  
  
6.  在**添加现有项**对话框中，打开的文件扩展名的列表，然后选择**所有文件 (\*。\*)**.  
  
7.  在目录中包含 BaseSharePointProject 项目，选择命名为 key.snk 文件，然后选择**添加**按钮。  
  
    > [!NOTE]  
    >  在本演练中，你创建的项目模板使用相同的 key.snk 文件进行签名使用模板创建的每个项目。 若要了解如何扩展此示例以便创建不同的 key.snk 文件，为每个项目实例，请参阅[演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
8.  重复步骤 5-8 以添加 BaseSharePointProject 目录中指定的子文件夹中的以下文件：  
  
    -   \Field1\Elements.xml  
  
    -   \Field1\SharePointProjectItem.spdata  
  
    -   \Features\Feature1\Feature1.feature  
  
    -   \Features\Feature1\Feature1.Template.xml  
  
    -   \Package\Package.package  
  
    -   \Package\Package.Template.xml  
  
     这些文件将直接添加到 SiteColumnProjectTemplate 项目中;不重新创建该项目中 Field1、 功能或包的子文件夹。 有关这些文件的详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>若要配置开发人员如何发现新项目对话框中的项目模板  
  
1.  在**解决方案资源管理器**，打开快捷菜单**SiteColumnProjectTemplate**项目节点，，然后选择**卸载项目**。 如果提示你将更改保存到任何文件，选择**是**按钮。  
  
2.  打开的快捷菜单**SiteColumnProjectTemplate**节点再次，然后选择**编辑 SiteColumnProjectTemplate.csproj**或**编辑 SiteColumnProjectTemplate.vbproj**.  
  
3.  在项目文件中，找到以下`VSTemplate`元素。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  用下列 XML 替换此元素。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`元素指定其他文件夹中生成项目时在其下创建的项目模板的路径。 此处指定的文件夹确保仅在客户打开时，将导致项目模板可用**新项目**对话框框中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
5.  保存并关闭文件。  
  
6.  在**解决方案资源管理器**，打开快捷菜单**SiteColumnProjectTemplate**项目，，然后选择**重新加载项目**。  
  
## <a name="editing-the-project-template-files"></a>编辑项目模板文件  
 在 SiteColumnProjectTemplate 项目中，编辑以下文件以定义项目模板的行为：  
  
-   AssemblyInfo.cs 或 AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj 或 ProjectTemplate.vbproj  
  
 在下面的过程中，你将添加到其中某些文件的可替换参数。 可替换参数是一个标记，用于开始和结束的美元符号 （$） 字符。 当用户使用此项目模板创建项目时，Visual Studio 自动将新项目中的这些参数替换具有特定值。 有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>若要编辑的 AssemblyInfo.cs 或 AssemblyInfo.vb 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，打开 AssemblyInfo.cs 或 AssemblyInfo.vb 文件中，然后将以下语句添加到它的顶部：  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     当**沙盒解决方案**SharePoint 项目的属性设置为**True**，Visual Studio 将添加<xref:System.Security.AllowPartiallyTrustedCallersAttribute>AssemblyInfo 代码文件。 但是，不能导入的项目模板中的 AssemblyInfo 代码文件<xref:System.Security>默认的命名空间。 你必须添加此**使用**或**导入**语句来阻止编译错误。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-elementsxml-file"></a>若要编辑的 Elements.xml 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用下列 XML 替换 Elements.xml 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 将添加`Field`定义网站栏、 其基类型和在其中列出库中的站点列组的名称的元素。 此文件的内容的详细信息，请参阅[字段定义架构](http://go.microsoft.com/fwlink/?LinkId=184290)。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>若要编辑 SharePointProjectItem.spdata 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用下列 XML 替换 SharePointProjectItem.spdata 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新的 XML 将对文件做出以下更改：  
  
    -   更改`Type`属性`ProjectItem`元素为相同字符串传递给<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>在项目项定义 (`SiteColumnProjectItemTypeProvider`在本演练前面创建的类)。  
  
    -   删除`SupportedTrustLevels`和`SupportedDeploymentScopes`属性从`ProjectItem`元素。 这些属性值是不必要的因为中指定的信任级别和部署范围`SiteColumnProjectItemTypeProvider`ProjectItemTypeDefinition 项目中的类。  
  
     .Spdata 文件的内容的详细信息，请参阅[SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-feature1feature-file"></a>若要编辑 Feature1.feature 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用下列 XML 替换 Feature1.feature 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     新的 XML 将对文件做出以下更改：  
  
    -   更改的值`Id`和`featureId`属性`feature`元素`$guid4$`。  
  
    -   更改的值`itemId`属性`projectItemReference`元素`$guid2$`。  
  
     有关.feature 文件的详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-packagepackage-file"></a>若要编辑 Package.package 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用下列 XML 替换 Package.package 文件的内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新的 XML 将对文件做出以下更改：  
  
    -   更改的值`Id`和`solutionId`属性`package`元素`$guid3$`。  
  
    -   更改的值`itemId`属性`featureReference`元素`$guid4$`。  
  
     有关.package 文件的详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>若要编辑 SiteColumnProjectTemplate.vstemplate 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，替换 SiteColumnProjectTemplate.vstemplate 文件的内容的 XML 的以下各节。  
  
    -   如果你要创建 Visual C# 项目模板，使用下面的 XML。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   如果你要创建 Visual Basic 项目模板，使用下面的 XML。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     新的 XML 将对文件做出以下更改：  
  
    -   集`Name`元素为值**网站栏**。 (此名称将显示在**新项目**对话框)。  
  
    -   将添加`ProjectItem`的每个 filethat 元素的包含在每个项目实例。  
  
    -   使用命名空间"http://schemas.microsoft.com/developer/vstemplate/2005"。 此解决方案中的其他项目文件使用"http://schemas.microsoft.com/developer/msbuild/2003"命名空间。 因此，将生成 XML 架构警告消息，但你可以在本演练中忽略它们。  
  
     有关.vstemplate 文件的内容的详细信息，请参阅[Visual Studio 模板架构参考](/visualstudio/extensibility/visual-studio-template-schema-reference)。  
  
2.  保存并关闭文件。  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>若要编辑的 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，替换 ProjectTemplate.csproj 文件或 ProjectTemplate.vbproj 文件的内容的 XML 的以下各节。  
  
    -   如果你要创建 Visual C# 项目模板，使用下面的 XML。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  如果你要创建 Visual Basic 项目模板，使用下面的 XML。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     新的 XML 将对文件做出以下更改：  
  
    -   使用`TargetFrameworkVersion`元素指定.NET Framework 3.5，不是 4.5。  
  
    -   将添加`SignAssembly`和`AssemblyOriginatorKeyFile`要签名的项目输出的元素。  
  
    -   将添加`Reference`程序集的元素引用该 SharePoint 项目使用。  
  
    -   在项目中，如 Elements.xml 和 SharePointProjectItem.spdata 添加为每个默认文件的元素。  
  
2.  保存并关闭文件。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-template"></a>创建 VSIX 包来部署项目模板  
 若要将扩展部署，使用中的 VSIX 项目**SiteColumnProjectItem**解决方案以创建 VSIX 包。 首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件中配置 VSIX 包。 然后，通过生成解决方案中创建 VSIX 包。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要配置并创建 VSIX 包  
  
1.  在**解决方案资源管理器**中**SiteColumnProjectItem**项目中，在清单编辑器中打开 source.extension.vsixmanifest 文件。  
  
     Source.extension.vsixmanifest 文件是所有的 VSIX 包需要 extension.vsixmanifest 文件的基础。 有关此文件的详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**产品名称**框中，输入**网站栏**。  
  
3.  在**作者**框中，输入**Contoso**。  
  
4.  在**说明**框中，输入**用于创建网站栏的 SharePoint 项目**。  
  
5.  选择**资产**选项卡上，然后选择**新建**按钮。  
  
     **添加新资产**对话框随即打开。  
  
6.  在**类型**列表中，选择**Microsoft.VisualStudio.ProjectTemplate**。  
  
    > [!NOTE]  
    >  此值对应于`ProjectTemplate`extension.vsixmanifest 文件中的元素。 此元素标识的子文件夹中包含的项目模板的 VSIX 包。 有关详细信息，请参阅[ProjectTemplate 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)。  
  
7.  在**源**列表中，选择**当前解决方案中的项目**。  
  
8.  在**项目**列表，并选择**SiteColumnProjectTemplate**，然后选择**确定**按钮。  
  
9. 选择**新建**再次按钮。  
  
     **添加新资产**对话框随即打开。  
  
10. 在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于`MefComponent`extension.vsixmanifest 文件中的元素。 此元素指定的 VSIX 包中的扩展程序集的名称。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在**源**列表中，选择**当前解决方案中的项目**。  
  
12. 在**项目**列表中，选择**ProjectItemTypeDefinition**，然后选择**确定**按钮。  
  
13. 在菜单栏上，选择**生成**，**生成解决方案**，并确保该项目在编译时没有错误。  
  
## <a name="testing-the-project-template"></a>测试项目模板  
 现在你就可以测试项目模板。 首先，开始调试 Visual Studio 的实验实例中的 SiteColumnProjectItem 解决方案。 然后，测试**网站栏**Visual Studio 的实验实例中的项目。 最后，生成并运行 SharePoint 项目，以验证站点列按预期方式工作。  
  
#### <a name="to-start-debugging-the-solution"></a>若要开始调试解决方案  
  
1.  使用管理凭据，重新启动 Visual Studio，然后打开 SiteColumnProjectItem 解决方案。  
  
2.  
  
3.  在 SiteColumnProjectItemTypeProvider 代码文件中，将断点添加到代码中的第一行`InitializeType`方法，然后选择**F5**键开始调试。  
  
     Visual Studio 将在 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 安装扩展，并启动 Visual Studio 的实验实例。 在 Visual Studio 的此实例中，将测试项目项。  
  
#### <a name="to-test-the-project-in-visual-studio"></a>在 Visual Studio 中测试项目  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  展开**Visual C#**或**Visual Basic**节点 （具体取决于你的项目模板支持的语言），展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在项目模板列表中，选择**网站栏**模板。  
  
4.  在**名称**框中，输入**SiteColumnTest** ，然后选择**确定**按钮。  
  
     在**解决方案资源管理器**，新项目将出现名为的项目项与**Field1**。  
  
5.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`InitializeType`方法，然后选择**F5**键继续调试项目。  
  
6.  在**解决方案资源管理器**，选择**Field1**节点，然后选择**F4**密钥。  
  
     **属性**窗口随即打开。  
  
7.  在属性列表中，确认属性**示例属性**显示。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>若要在 SharePoint 中测试的网站栏  
  
1.  在**解决方案资源管理器**，选择**SiteColumnTest**节点。  
  
2.  在**属性**窗口中的，在文本框中旁**站点 URL**属性，输入**http://localhost**。  
  
     此步骤指定你想要用于调试的开发计算机上的本地 SharePoint 站点。  
  
    > [!NOTE]  
    >  **站点 URL**属性为空默认情况下，因为网站栏项目模板不提供向导创建项目时收集此值。 若要了解如何添加向导，要求开发人员提供此值，然后在新项目中配置此属性，请参阅[演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
3.  选择**F5**密钥。  
  
     打包和部署到 SharePoint 站点中指定的网站栏**站点 URL**项目属性。 Web 浏览器将打开到此站点的默认页面。  
  
    > [!NOTE]  
    >  如果**脚本调试已禁用**对话框出现时，选择**是**按钮以继续调试项目。  
  
4.  上**站点操作**菜单上，选择**站点设置**。  
  
5.  上**站点设置**页上，在**库**列表中，选择**站点列**链接。  
  
6.  在站点列列表中，确认**自定义列**组包含名为的列**SiteColumnTest**。  
  
7.  关闭 web 浏览器。  
  
## <a name="cleaning-up-the-development-computer"></a>清理开发计算机  
 在完成测试项目后，从 Visual Studio 的实验实例中删除项目模板。  
  
#### <a name="to-clean-up-the-development-computer"></a>若要清理的开发计算机  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**网站栏**扩展，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**按钮，以确认你想要卸载扩展。  
  
4.  选择**关闭**按钮以完成卸载。  
  
5.  关闭 Visual Studio （实验实例和 SiteColumnProjectItem 解决方案处于打开状态的 Visual Studio 的实例） 的两个实例。  
  
## <a name="next-steps"></a>后续步骤  
 完成本演练后，你可以将向导添加到项目模板。 当用户创建网站栏项目时，向导将要求用户提供网站 URL 以用于调试和新的解决方案是否为沙盒解决方案，并向导将新的项目配置使用此信息。 该向导还收集有关列 （如基类型和在其中列出网站栏库中的列组） 的信息，并将此信息添加到新的项目中的 Elements.xml 文件。 有关详细信息，请参阅[演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## <a name="see-also"></a>另请参阅  
 [演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [为 SharePoint 项目项创建项模板和项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [扩展 SharePoint 项目系统中保存数据](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [将自定义数据与 SharePoint 工具扩展相关联](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  