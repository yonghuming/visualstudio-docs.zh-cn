---
title: "演练：使用项目模板创建网站栏项目项（第 1 部分）"
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
  - "SharePoint 项目项，定义自己的类型"
  - "项目项 [Visual Studio 中的 SharePoint 开发]，定义自己的类型"
  - "SharePoint 项目，创建自定义模板"
  - "Visual Studio 中的 SharePoint 开发，定义新项目项类型"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# 演练：使用项目模板创建网站栏项目项（第 1 部分）
  SharePoint 项目是包含一个或多个 SharePoint 项目项的容器。  在 Visual Studio 中，您可以通过创建您自己的 SharePoint 项目项类型，然后将其与某个项目模板相关联，从而扩展 SharePoint 项目系统。  在本演练中，您将定义一个用于创建网站栏的项目项类型，然后将创建一个可用于创建包含网站栏项目项的新项目的项目模板。  
  
 本演练将演示以下任务：  
  
-   创建一个为网站栏定义新类型的 SharePoint 项目项的 Visual Studio 扩展。  项目项类型包含一个在**“属性”**窗口中显示的简单的自定义属性。  
  
-   为项目项创建 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 项目模板。  
  
-   生成 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包以部署项目模板和扩展程序集。  
  
-   调试并测试项目项。  
  
 这是一个独立的演练。  完成本演练后，可以向项目模板添加向导来增强项目项。  有关详细信息，请参阅[演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
> [!NOTE]  
>  可从以下位置下载一个示例，该示例包含此演练的已完成项目、代码和其他文件： [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   支持的 Microsoft Windows、SharePoint 和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关详细信息，请参阅[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   SharePoint 中的网站栏。  有关更多信息，请参见 [列](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
-   Visual Studio 中的项目模板。  有关详细信息，请参阅[在 Visual Studio 中创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)。  
  
## 创建项目  
 若要完成本演练，您需要创建以下三个项目：  
  
-   一个 VSIX 项目。  此项目创建 VSIX 包来部署网站栏项目项和项目模板。  
  
-   一个项目模板项目。  此项目创建一个项目模板，该项目模板可用于创建包含网站栏项目项的新 SharePoint 项目。  
  
-   一个类库项目。  此项目实现一个定义网站栏项目项的行为的 Visual Studio 扩展。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在 "新项目" 对话框顶部，确保 **.NET Framework 4.5** 在 .NET Framework 的版本列表中选中。  
  
4.  展开**“Visual Basic”**或**“Visual C\#”**节点，然后选择“扩展性”节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio 2010 SDK 之后，“扩展性”节点才可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
5.  在项目模板列表中，选择**“VSIX项目”**。  
  
6.  在“名称”框中，输入**SiteColumnProjectItem**，然后选择“确定”按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“SiteColumnProjectItem”**项目添加到**“解决方案资源管理器”**中。  
  
#### 创建项目模板项目  
  
1.  在“解决方案资源管理器”中，打开解决方案节点的快捷菜单，依次选择**“添加”**、**“新项目”**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在 "新项目" 对话框顶部，确保 **.NET Framework 4.5** 在 .NET Framework 的版本列表中选中。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**节点，然后选择“扩展性”节点。  
  
4.  在项目模板的列表中，选择**“C\# 项目模板”**或**“Visual Basic 项目模板”**模板。  
  
5.  在“名称”框中，输入**SiteColumnProjectTemplate**，然后选择“确定”按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“SiteColumnProjectTemplate”**项目添加到解决方案中。  
  
6.  从项目中删除 Class1 代码文件。  
  
7.  如果创建了 Visual Basic 项目，则还从该项目中删除以下文件：  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### 创建扩展项目  
  
1.  在“解决方案资源管理器”中，打开解决方案节点的快捷菜单，依次选择**“添加”**、**“新项目”**。  
  
2.  在 "新项目" 对话框顶部，确保 **.NET Framework 4.5** 在 .NET Framework 的版本列表中选中。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**节点，选择**Windows**节点，然后选择“类库”模板。  
  
4.  在“名称”框中，输入**ProjectItemTypeDefinition**，然后选择“确定”按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“ProjectItemTypeDefinition”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置扩展项目  
 添加代码文件和程序集引用以配置扩展项目。  
  
#### 配置项目  
  
1.  在 ProjectItemTypeDefinition 项目中，添加名为 **SiteColumnProjectItemTypeProvider** 的代码文件。  
  
2.  在菜单栏上，依次选择“项目”、“添加引用”。  
  
3.  在“引用管理器\-项目类型定义”对话框中，展开“程序集”节点，选中“框架”节点，然后选中“ComponentModel.Composition”复选框。  
  
4.  选择 “扩展” 节点，选择 Microsoft.VisualStudio.SharePoint 程序集旁边的复选框，然后选择“确定” 按钮。  
  
## 定义新的 SharePoint 项目项类型  
 创建一个类，该类实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口以定义新项目项类型的行为。  每当需要定义新类型的项目项时，就要实现此接口。  
  
#### 定义新的 SharePoint 项目项类型  
  
1.  在**SiteColumnProjectItemTypeProvider**代码文件，用以下代码替换默认代码，然后保存文件。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## 创建 Visual Studio 项目模板  
 通过创建一个项目模板，您能够使其他开发人员创建包含网站栏项目项的 SharePoint 项目。  SharePoint 项目模板包含 Visual Studio 中的所有项目所需的文件，例如，.csproj 或 .vbproj 和 .vstemplate 文件，以及特定于 SharePoint 项目的文件。  有关详细信息，请参阅[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 在此过程中，您将创建一个空 SharePoint 项目，生成特定于 SharePoint 项目的文件。  然后将这些文件添加到 SiteColumnProjectTemplate 项目中，以便从此项目生成的模板。  另外，配置 SiteColumnProjectTemplate 项目文件，以指定项目模板显示在“新项目”对话框中的位置。  
  
#### 为项目模板创建文件  
  
1.  利用管理凭据启动第二个 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 实例。  
  
2.  新建名为 **BaseSharePointProject** 的 SharePoint 2010 项目。  
  
    > [!IMPORTANT]  
    >  在“SharePoint 自定义向导”中，不要选择**“部署为场解决方案”**选项按钮。  
  
3.  在项目中添加一个空的元素项，然后为项命名为“字段1”。  
  
4.  保存该项目，然后关闭第二个 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 实例。  
  
5.  在具有SiteColumnProjectItem解决方案的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]实例，在“解决方案资源管理器”中，打开**SiteColumnProjectTemplate**项目节点的快捷菜单，选择“添加”，然后选择“现有项目”。  
  
6.  在“添加现有项”对话框中，开启文件扩展名的下拉列表，然后选择“所有文件\(\*.\*\)”。  
  
7.  在包含BaseSharePointProject项目的目录，选择key.snk文件，然后选择”添加“按钮。  
  
    > [!NOTE]  
    >  在本演练中，您创建的项目模板使用同一个 key.snk 文件来对使用该模板创建的每个项目进行签名。  若要了解如何扩展此示例以便为每个项目实例创建不同的 key.snk 文件，请参见[演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
8.  重复步骤 5\-8 以从 BaseSharePointProject 目录中的指定子文件夹添加下列文件：  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     将这些文件直接添加到 SiteColumnProjectTemplate 项目中；不要在该项目中重新创建 Field1、Features 或 Package 子文件夹。  有关这些文件的更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
#### 配置开发人员在“新项目”对话框中发现项目模板的方式  
  
1.  在“解决方案资源管理器”中，开启**SiteColumnProjectTemplate**项目节点的快捷菜单，选择”卸载项目“。  如果提示您保存对任何文件的更改，则选择“是”按钮。  
  
2.  开启**“SiteColumnProjectTemplate”**节点的快捷菜单，然后选择**“编辑 SiteColumnProjectTemplate.csproj”**或**“编辑 SiteColumnProjectTemplate.vbproj”**。  
  
3.  定位到项目文件中的下列`VSTemplate` 元素。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  用下面的内容替换这个元素。  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 元素指定路径中的其他文件夹，在生成项目时将在这些文件夹中创建项目模板。  此处指定的文件夹确保项目模板将只有当客户打开"新建项目"对话框时可用，展开了**SharePoint**节点，然后选择**2010**节点。  
  
5.  保存并关闭文件。  
  
6.  在“解决方案资源管理器”中，打开**SiteColumnProjectTemplate**项目的快捷菜单，然后选择“重新加载项目”。  
  
## 编辑项目模板文件  
 编辑 SiteColumnProjectTemplate 项目中的下列文件以定义项目模板的行为：  
  
-   AssemblyInfo.cs 或 AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj 或 ProjectTemplate.vbproj  
  
 在下面的过程中，将向这些文件中的某些文件添加可替换的参数。  可替换参数是以美元符号 \($\) 字符作为开始和结束的标记。  当用户使用此项目模板创建新项目时，Visual Studio 会自动将新项目中的这些参数替换为特定值。  有关详细信息，请参阅[可替换参数](../sharepoint/replaceable-parameters.md)。  
  
#### 编辑 AssemblyInfo.cs 或 AssemblyInfo.vb 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，打开 AssemblyInfo.cs 或 AssemblyInfo.vb 文件，然后在顶级添加以下语句：  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     当 SharePoint 项目的**“沙盒解决方案”**属性设置为**“True”** 时，Visual Studio 会将 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 添加到 AssemblyInfo 代码文件中。  但默认情况下，项目模板中的 AssemblyInfo 代码文件不会导入 <xref:System.Security> 命名空间。  必须添加此 **using** 或 **Imports** 语句以防止编译错误。  
  
2.  保存并关闭文件。  
  
#### 编辑 Elements.xml 文件  
  
1.  在SiteColumnProjectTemplate项目中，用下面的 XML 替换 Elements.xml 文件的内容。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     新的 XML 会添加一个 `Field` 元素，该元素定义网站栏的名称、基类型以及将在其中列出库中的网站栏的组。  有关文件内容的详细信息，请参阅[Field Definition Schema](http://go.microsoft.com/fwlink/?LinkId=184290)。  
  
2.  保存并关闭文件。  
  
#### 编辑 SharePointProjectItem.spdata 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用以下 XML 替换 SharePointProjectItem.spdata 文件的内容。  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新 XML 将对此文件进行以下更改：  
  
    -   将 `ProjectItem` 元素的 `Type` 特性更改为传递给项目项定义（在本演练中先前创建的 `SiteColumnProjectItemTypeProvider` 类）上的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的同一字符串。  
  
    -   从 `ProjectItem` 元素中移除 `SupportedTrustLevels` 和 `SupportedDeploymentScopes` 特性。  由于信任级别和部署范围是在 ProjectItemTypeDefinition 项目的 `SiteColumnProjectItemTypeProvider` 类中指定的，因此这些特性值不是必需的。  
  
     有关 .spdata 文件的内容的更多信息，请参见 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
2.  保存并关闭文件。  
  
#### 编辑 Feature1.feature 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用以下 XML 替换 Feature1.feature 文件的内容。  
  
    ```  
  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     新 XML 将对此文件进行以下更改：  
  
    -   将 `feature` 元素的 `Id` 和 `featureId` 特性的值更改为 `$guid4$`。  
  
    -   将 `projectItemReference` 元素的 `itemId` 特性的值更改为 `$guid2$`。  
  
     有关 .feature 文件的更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  保存并关闭文件。  
  
#### 编辑 Package.package 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，用以下 XML 替换 Package.package 文件的内容。  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新 XML 将对此文件进行以下更改：  
  
    -   将 `package` 元素的 `Id` 和 `solutionId` 特性的值更改为 `$guid3$`。  
  
    -   将 `featureReference` 元素的 `itemId` 特性的值更改为 `$guid4$`。  
  
     有关 .package 文件的更多信息，请参见[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  保存并关闭文件。  
  
#### 编辑 SiteColumnProjectTemplate.vstemplate 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，请使用 XML 替换为以下某一部分的 SiteColumnProjectTemplate.vstemplate 文件的内容。  
  
    -   如果您要创建 Visual C\# 项目模板，则使用以下 XML。  
  
    ```  
  
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
  
    -   如果您要创建 Visual Basic 项目模板，则使用以下 XML。  
  
    ```  
  
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
  
     新 XML 将对此文件进行以下更改：  
  
    -   设置`Name`元素的值为”网站栏“。（这个名称出现在“新建项目”对话框中）。  
  
    -   为每个项目实例中包含的每个文件添加 `ProjectItem` 元素。  
  
    -   使用命名空间“http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005”。  此解决方案的其他项目文件使用“http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003”命名空间。  因此，XML 架构警告消息将生成，但是，在本演练中您可以忽略它们。  
  
     有关 .vstemplate 文件的内容的更多信息，请参见 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)。  
  
2.  保存并关闭文件。  
  
#### 编辑 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 文件  
  
1.  在 SiteColumnProjectTemplate 项目中，请使用 XML 替换为以下某一部分的文件 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 文件的内容。  
  
    -   如果您要创建 Visual C\# 项目模板，则使用以下 XML。  
  
    ```  
  
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
  
    1.  如果您要创建 Visual Basic 项目模板，则使用以下 XML。  
  
    ```  
  
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
  
     新 XML 将对此文件进行以下更改：  
  
    -   使用 `TargetFrameworkVersion` 元素以指定 .NET Framework 3.5，而不是4.5。  
  
    -   添加 `SignAssembly` 和 `AssemblyOriginatorKeyFile` 元素以对项目输出进行签名。  
  
    -   为 SharePoint 项目使用的程序集引用添加 `Reference` 元素。  
  
    -   为项目中的每个默认文件添加元素，如 Elements.xml 和 SharePointProjectItem.spdata。  
  
2.  保存并关闭文件。  
  
## 创建 VSIX 包以部署项目模板  
 若要部署扩展，请使用 **SiteColumnProjectItem** 解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后，通过生成解决方案来创建 VSIX 包。  
  
#### 配置并创建 VSIX 包  
  
1.  在“解决方案资源管理器”中，在 **SiteColumnProjectItem** 项目中，在清单文件编辑器中开启source.extension.vsixmanifest 文件。  
  
     source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在“产品名称”框中键入**“网站栏”**。  
  
3.  在“作者”框中键入 **Contoso**。  
  
4.  在“描述”框中键入“用于创建网站栏的 SharePoint 项目”。  
  
5.  选择“资产”标签，然后选择“新建”按钮。  
  
     打开“添加新资产”对话框。  
  
6.  在”类型“ 列表中，选择 **Microsoft.VisualStudio.ProjectTemplate**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `ProjectTemplate` 元素。  此元素标识包含项目模板的 VSIX 包中的子文件夹。  有关详细信息，请参阅[NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/87add64c-9dcd-495f-8815-209dab182cb1)。  
  
7.  在 “源” 列表中，选择 “当前解决方案中的项目”。  
  
8.  在“项目”列表中，选择**“SiteColumnProjectTemplate”（网站栏项目模板）**，然后选择“确定”按钮。  
  
9. 再次选择 “新建”按钮  
  
     打开“添加新资产”对话框。  
  
10. 在"类型" 列表中，选择 **Microsoft.VisualStudio.ItemTemplate**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关详细信息，请参阅[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在 “源” 列表中，选择 “当前解决方案中的项目”。  
  
12. 在“项目”列表中，选择**“ProjectItemTypeDefinition”（项目项类型定义）**，然后选择“确定”按钮。  
  
13. 在菜单栏上，依次选择”生成“，”生成解决方案“，然后确保项目在编译时不会出错。  
  
## 测试项目模板  
 现在您可以对项目模板进行测试了。  首先，在 Visual Studio 的实验实例中开始调试 SiteColumnProjectItem 解决方案。  然后，测试 Visual Studio 实验实例中的**“网站栏”**项目。  最后，生成并运行 SharePoint 项目，以验证此网站栏是否按预期工作。  
  
#### 开始调试解决方案  
  
1.  利用管理员证书重新启动 Visual Studio，然后打开 SiteColumnProjectItem 解决方案。  
  
2.  在SiteColumnProjectItemTypeProvider代码文件中，在`InitializeType`方法中的第一行代码中添加一个断点，然后选择**F5**键开始调试。  
  
     Visual Studio 会将扩展安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0 并启动 Visual Studio 的实验实例。  您将在此 Visual Studio 实例中测试项目项。  
  
#### 在 Visual Studio 中测试项目  
  
1.  在 Visual Studio 的实验实例中，在“文件”菜单上指向“新建”，然后单击“项目”。  
  
2.  展开 **Visual C\#**或**Visual Basic**节点\(具体取决于项目模板支持的语言\)，再展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
3.  在项目模板的列表中，选择“网站栏”模板。  
  
4.  在“名称”框中，输入 **SiteColumnTest**，然后选中“确定”按钮。  
  
     一个新项目将出现在**“解决方案资源管理器”**中，且有一个名为**“Field1”**的项目项。  
  
5.  验证在Visual Studio的其他实例的代码将停止在您之前在`InitializeType` 方法设置的断点，然后选择**F5**键来继续调试项目。  
  
6.  在”解决方案资源管理器“中，选择**Field1**节点，然后选择**F4**键。  
  
     这将打开**“属性”**窗口。  
  
7.  验证属性**“示例属性”**是否显示在属性列表中。  
  
#### 在 SharePoint 中测试网站栏  
  
1.  在“解决方案资源管理器”中，选择**“SiteColumnTest”（网站栏测试）**节点。  
  
2.  在“属性”窗口中，单击**“网站 URL”**属性旁边的文本框并键入 **http:\/\/localhost**。  
  
     此步骤在开发计算机上指定要用于调试的本地 SharePoint 网站。  
  
    > [!NOTE]  
    >  默认情况下**“网站 URL”**属性为空，因为“网站栏”项目模板不会提供用于在创建项目时收集此值的向导。  若要了解如何添加一个要求开发人员提供此值然后在新项目中配置此属性的向导，请参见[演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
3.  选择“F5”键。  
  
     这将对网站栏进行打包并将其部署到由项目的**“网站 URL”**属性指定的 SharePoint 网站中。  Web 浏览器将打开此网站的默认页。  
  
    > [!NOTE]  
    >  如果出现“脚本调试被禁用”对话框，请单击“是”继续调试该项目。  
  
4.  在“网站操作”菜单上，单击“网站设置”。  
  
5.  在“网站设置”页的“库”列表下，选择“网站栏”链接。  
  
6.  在网站栏的列表中，验证是否存在一个包含名为**“SiteColumnTest”**的”自定义列”组。  
  
7.  关闭 Web 浏览器。  
  
## 清理开发计算机  
 测试完项目之后，从 Visual Studio 的实验实例中移除项目模板。  
  
#### 清理开发计算机  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上选择 “工具”，“扩展和更新”。  
  
     “扩展和更新”对话框将打开。  
  
2.  在扩展列表中，选择 "网站栏"扩展，然后选择 "卸载" 按钮。  
  
3.  在出现的对话框中，单击“是”以确认您要卸载该扩展。  
  
4.  选择“关闭”按钮，完成卸载。  
  
5.  关闭 Visual Studio 的两个实例（Visual Studio 的实验实例和 Visual Studio 的已打开 SiteColumnProjectItem 解决方案的实例）。  
  
## 后续步骤  
 完成本演练后，可以向项目模板添加向导。  当用户创建“网站栏”项目时，该向导将要求用户提供网站 URL 以用于调试，并选择新解决方案是否为沙盒解决方案，然后该向导将使用这些信息配置新项目。  该向导还会收集有关列的信息（如基类型和将在其中列出网站栏库中的列的组），并将这些信息添加到新项目的 Elements.xml 文件中。  有关详细信息，请参阅[演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## 请参阅  
 [演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  