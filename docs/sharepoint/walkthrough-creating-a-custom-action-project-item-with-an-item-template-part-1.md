---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1"
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
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  可以通过在 Visual Studio 中创建自己的项目项类型来扩展 SharePoint 项目系统。  在本演练中，您将创建一个项目项，然后可将此项目项添加到 SharePoint 项目中以便在 SharePoint 网站上创建一个自定义操作。  该自定义操作可将一个菜单项添加到 SharePoint 网站的**“网站操作”**菜单中。  
  
 本演练将演示以下任务：  
  
-   创建一个 Visual Studio 扩展，该扩展为自定义操作定义了新类型的 SharePoint 项目项。  新的项目项类型将实现以下几个自定义功能：  
  
    -   用作与项目项相关的其他任务（如显示 Visual Studio 中用于自定义操作的设计器）的起始点的快捷菜单。  
  
    -   当开发人员更改项目项及其所在的项目的某些属性时运行的代码。  
  
    -   **“解决方案资源管理器”**中显示在项目项旁边的自定义图标。  
  
-   为项目项创建 Visual Studio 项目模板。  
  
-   生成 Visual Studio 扩展 \(VSIX\) 包以部署项目项模板和扩展程序集。  
  
-   调试并测试项目项。  
  
 这是一个独立的演练。  完成本演练后，可以向项模板添加向导来增强项目项。  有关详细信息，请参阅[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
> [!NOTE]  
>  可从以下位置下载一个示例，该示例包含此演练的已完成项目、代码和其他文件： [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   支持的 Microsoft Windows、SharePoint 和 Visual Studio 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关详细信息，请参阅[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   SharePoint 中的自定义操作。  有关详细信息，请参见 [自定义方法](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Visual Studio 中的项模板。  有关详细信息，请参阅[在 Visual Studio 中创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)。  
  
## 创建项目  
 若要完成本演练，您需要创建以下三个项目：  
  
-   一个 VSIX 项目。  该项目创建 VSIX 包以部署 SharePoint 项目项。  
  
-   一个项模板项目。  该项目创建一个可用于向 SharePoint 项目添加 SharePoint 项目项的项模板。  
  
-   一个类库项目。  该项目实现定义 SharePoint 项目项的行为的 Visual Studio 扩展。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在**“新建项目”**对话框顶部的列表中，确保选择上**“.NET Framework 4.5”**。  
  
4.  在**“新建项目”**对话框中，展开**“Visual C\#”**或**“Visual Basic”**节点，然后选择**“扩展性”**节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio 2010 SDK 之后，**“扩展性”**节点才可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
5.  选择 **VSIX 项目** 模板  
  
6.  在**“名称”**文本框中，输入 **CustomActionProjectItem**, 然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将**“CustomActionProjectItem”**项目添加到**“解决方案资源管理器”**中。  
  
#### 创建项模板项目  
  
1.  在**“解决方案资源管理器”**中，打开解决方案”节点的快捷菜单，依次选择**“添加”**、**“新项目”**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在**“新建项目”**对话框顶部的列表中，确保选择上**“.NET Framework 4.5”**。  
  
3.  在**“新建项目”**对话框中，展开**“Visual C\#”**或**“Visual Basic”**节点，然后选择**“扩展性”**节点。  
  
4.  在项目模板列表中，选择**“C\# 项模板”**或**“Visual Basic 项模板”**。  
  
5.  在**“名称”**文本框中，输入**“项模板”**，然后选择**“确定”**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“ItemTemplate”**项目添加到解决方案中。  
  
#### 创建扩展项目  
  
1.  在**“解决方案资源管理器”**中，打开解决方案”节点的快捷菜单，依次选择**“添加”**、**“新项目”**。  
  
2.  在**“新建项目”**对话框顶部的列表中，确保选择上**“.NET Framework 4.5”**。  
  
3.  在**“新建项目”**对话框中，展开**“Visual C\#”**或**“Visual Basic”**节点，选择“**Windows”**节点，然后选择**“类库”**模板。  
  
4.  在**“名称”**文本框中，输入**项目项定义**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“ProjectItemDefinition”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置扩展项目  
 在编写代码以定义 SharePoint 项目项类型之前，您必须将代码文件和程序集引用添加到扩展项目中。  
  
#### 配置项目  
  
1.  在**“解决方案资源管理器”**中，打开 **项目项定义** 项目的快捷菜单，选择 **“添加”**, 然后选择**“新建项目”**.  
  
2.  在项目项的列表中，单击**“代码文件”**。  
  
3.  在 **名称** 框中，输入适于文件扩展名的 **自定义方法** 的名字，然后选择 **添加** 按钮。  
  
4.  在**“解决方案资源管理器”**中，打开项目的 **项目项自定义** 的快捷菜单，然后选择**“添加引用”**。  
  
5.  在 **引用管理器– 项目项自定义** 对话框中，选择 **程序集** 节点，然后选择 **框架** 节点。  
  
6.  选中下面每个程序集旁边的复选框：  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  选择 **扩展** 节点，请在 Microsoft.VisualStudio.Sharepoint 程序集旁边的下选择框，然后选择 **确定** 按钮。  
  
## 定义新的 SharePoint 项目项类型  
 创建一个类，该类实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口以定义新项目项类型的行为。  每当需要定义新类型的项目项时，就要实现此接口。  
  
#### 定义新的 SharePoint 项目项类型  
  
1.  在 ProjectItemDefinition 项目中，打开 CustomAction 代码文件。  
  
2.  将此文件中的代码替换为以下代码。  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## 在解决方案资源管理器中为项目项创建图标  
 在创建一个自定义 SharePoint 项目项时，您可以将一个图像（图标或位图）与该项目项相关联。  在**“解决方案资源管理器”**中，此图像会出现在该项目项的旁边。  
  
 在下面的过程中，您将为项目项创建一个图标，并将此图标嵌入到扩展程序集中。  先前创建的 `CustomActionProjectItemTypeProvider` 类的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> 将引用此图标。  
  
#### 为项目项创建自定义图标  
  
1.  在**“解决方案资源管理器”**中，打开项目的 **项目项自定义** 的快捷菜单，选择然后选择**添加**,然后选择 **“新建项目”**.  
  
2.  在项目项的列表中，选择 **图标文件** 项。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，必须单击**“常规”**节点才能查看**“图标文件”**项。  
  
3.  在**“名称”**框中输入 **CustomAction\_SolutionExplorer.ico**, 然后选择 **“添加”** 按钮。  
  
     新图标将在**“图像编辑器”**中打开。  
  
4.  编辑 16x16 版本的图标文件，使得设计出的图标可以让您识别，然后保存该图标文件。  
  
5.  在**“解决方案资源管理器”**中，单击**“CustomAction\_SolutionExplorer.ico”**。  
  
6.  在 **属性** 窗口，选择 **生成方法** 属性旁边的箭头。  
  
7.  在显示的列表中，选择 **嵌入的资源**。  
  
## 检查点  
 演练进行到此时，项目项的所有代码都位于项目中。  生成项目以确保编译项目时不会出错。  
  
#### 生成项目  
  
1.  打开 **项目项自定义** 项目的快捷菜单，然后选择 **“生成”**.  
  
## 创建 Visual Studio 项模板  
 若要使其他开发人员能够使用您的项目项，必须创建一个项目模板或项模板。  开发人员可在 Visual Studio 中使用这些模板，通过创建一个新项目或向现有项目中添加项，从而创建您的项目项的实例。  在本演练中，将使用 ItemTemplate 项目配置项目项。  
  
#### 创建项模板  
  
1.  从 ItemTemplate 项目中删除 Class1 代码文件。  
  
2.  在 ItemTemplate 项目中，打开 ItemTemplate.vstemplate 文件。  
  
3.  用下面的 XML 替换该文件的内容，然后保存并关闭该文件。  
  
    > [!NOTE]  
    >  下面的 XML 适用于 Visual C\# 项模板。  如果创建的是 Visual Basic 项模板，请用 `VisualBasic` 替换 `ProjectType` 元素的值。  
  
    ```  
  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     此文件定义了项模板的内容和行为。  有关此文件的内容的更多信息，请参见 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)。  
  
4.  在**“解决方案资源管理器”**中，打开**项模板**解决方案节点的快捷菜单，选择**“添加”**，然后选择**新建项目**.  
  
5.  在**“添加新项”**对话框中单击**“文本文件”** 模板。  
  
6.  在**“名称”**框中输入 **CustomAction.spdata**, 然后选择 **“添加”**按钮。  
  
7.  向 CustomAction.spdata 文件添加下面的 XML，然后保存并关闭该文件。  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     此文件包含有关项目项所包含的文件的信息。  `ProjectItem` 元素的 `Type` 特性必须设置为传递给项目项定义（在本演练中先前创建的 `CustomActionProjectItemTypeProvider` 类）上的 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的同一字符串。  有关 .spdata 文件的内容的更多信息，请参见 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
8.  在**“解决方案资源管理器”**中，打开**项模板**解决方案节点的快捷菜单，选择**“添加”**，然后选择**新建项目**.  
  
9. 在 **“添加新项”** 对话框中选择 **“XML 文件”**。  
  
10. 在**“名称”**框中输入 **Elements.xml**, 然后选择 **“添加”** 按钮。  
  
11. 用下面的 XML 替换 Elements.xml 文件的内容，然后保存并关闭该文件。  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     此文件定义了一个默认自定义操作，该操作会在 SharePoint 网站的**“网站操作”**菜单上创建一个菜单项。  当用户单击此菜单项时，Web 浏览器中将打开 `UrlAction` 元素中指定的 URL。  有关使用 XML 元素定义自定义操作的详细信息，请参见 [自定义事件定义](http://go.microsoft.com/fwlink/?LinkId=177801)的 XML 元素。  
  
12. 可以选择打开并修改 ItemTemplate.ico 文件，使该文件具有可识别的设计。  在**“添加新项”**对话框中，此图标将显示在该项目项的旁边。  
  
13. 在**“解决方案资源管理器”**中，打开项目的 **“项模板”** 快捷菜单，然后选择 **卸载项目**.  
  
14. 再次打开 **项目项** 项目的快捷菜单，然后选择 **编辑 ItemTemplate.csproj** 或 **编辑 ItemTemplate.vbproj**。  
  
15. 定位到项目文件中的以下 `VSTemplate` 元素。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. 用下面的 XML 替换 `VSTemplate` 元素，然后保存并关闭该文件。  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` 元素指定路径中的其他文件夹，在生成项目时将在这些文件夹中创建项模板。  此处指定的文件夹确保项模板只适用于当顾客打开 **添加新项** 对话框，展开 **SharePoint** 节点并选择 **2010** 节点的时候.  
  
17. 在**“解决方案资源管理器”**中，打开 **“项模板”** 的快捷菜单，然后选择 **重新加载项目**.  
  
## 创建 VSIX 包以部署项目项  
 若要部署扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后，通过生成解决方案来创建 VSIX 包。  
  
#### 配置并创建 VSIX 包  
  
1.  在**“解决方案资源管理器”**中打开 CustomActionProjectItem 项目中的 **source.extension.vsixmanifest** 文件的快捷菜单，选择 **“新建项”**。  
  
     Visual Studio 将在清单编辑器中打开该文件。  source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**“产品名称”**框中键入**“自定义操作项目项”**。  
  
3.  在**“作者”**框中键入 **Contoso**。  
  
4.  在**“说明”**框中，键入**“表示自定义操作的 SharePoint 项目项”**。  
  
5.  在 **资产** 选项卡中，选择 **新建** 按钮。  
  
     **“添加新项”**对话框随即出现。  
  
6.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.ItemTemplate**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `ItemTemplate` 元素。  此元素标识包含项目项模板的 VSIX 包中的子文件夹。  有关详细信息，请参阅[NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
8.  在**“屏幕数据”**列表中，选择**“项模板”**，然后选择**“确定”**按钮。  
  
9. 在 **资产** 选项，请选择 **新建** 按钮。  
  
     **“添加新项”**对话框随即出现。  
  
10. 在 **类型** 列表中，选择 **Microsoft.VisualStudio.ItemTemplate**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关详细信息，请参阅[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
12. 在 **项目** 列表中，选择 **ProjectItemDefinition**。  
  
13. 选择**“确定”**按钮。  
  
14. 在菜单栏上，依次选择 **生成**，**生成解决方案**，然后确保项目在编译时不会出错。  
  
15. 确保 CustomActionProjectItem 项目的生成输出文件夹包含 CustomActionProjectItem.vsix 文件。  
  
     默认情况下，生成输出文件夹为..\\bin\\debug 文件夹, 包含 CustomActionProjectItem 项目的文件夹下。  
  
## 测试项目项  
 现在您可以对项目项进行测试了。  首先，在 Visual Studio 的实验实例中开始调试 CustomActionProjectItem 解决方案。  然后，测试 Visual Studio 实验实例中的 SharePoint 项目中的**“自定义操作”**项目项。  最后，生成并运行 SharePoint 项目，以验证此自定义操作是否按预期工作。  
  
#### 开始调试解决方案  
  
1.  使用管理员权限重新启动 Visual Studio，并打开“CustomActionProjectItem”解决方案。  
  
2.  打开 CustomAction 代码文件，并在 `InitializeType` 方法的第一行代码中添加一个断点。  
  
3.  选择 **F5** 键开始调试。  
  
     Visual Studio 将扩展安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0 中，并启动 Visual Studio 的实验实例。  您将在此 Visual Studio 实例中测试项目项。  
  
#### 在 Visual Studio 中测试项目项  
  
1.  在 Visual Studio 的实验实例中，在**“文件”**菜单上指向**“新建”**，然后单击**“项目”**。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**（取决于项模板支持的语言），再展开**“SharePoint”**，然后单击**“2010”** 节点。  
  
3.  在项目模板的列表中，单击**“SharePoint 2010 项目”**。  
  
4.  在 **“名称”** 框中，输入**“CreateExcelWorkbook”**，然后选则 **“确定”** 按钮。  
  
5.  在**“SharePoint 自定义向导”**中，键入要用于调试的网站的 URL，并单击**“完成”** 按钮。  
  
6.  在**“解决方案资源管理器”**中，打开项目节点的快捷菜单，选择**“添加”**，然后选择**“新建项目”**。  
  
7.  在**“添加新项”**对话框中，单击**“SharePoint”**节点下的**“2010”**节点。  
  
     确认**“自定义操作”**项显示在项目项的列表中。  
  
8.  选择 **自定义操作** 项，然后选择 **添加** 按钮。  
  
     Visual Studio 会将名为**“CustomAction1”**的新项添加到项目中，并在编辑器中打开 Elements.xml 文件。  
  
9. 验证另一个 Visual Studio 实例中的代码是否会在您之前在 `InitializeType` 方法中设置的断点处停止。  
  
10. 选择 **F5** 键继续调试项目。  
  
11. 在 Visual Studio 的实验实例中，在**“解决方案资源管理器”**中，打开 **“CustomAction1”** 节点的快捷菜单，再单击**“查看自定义操作设计器”**。  
  
12. 确认会出现一个消息框，然后单击**“确定”**。  
  
     可以使用此快捷菜单为开发人员提供其他选项或命令，如显示用于自定义操作的设计器。  
  
13. 在菜单栏上，依次选择**“视图”**、**“输出”**。  
  
     将打开**“输出”**窗口。  
  
14. 在 **解决方案资源管理器** 中，打开 **CustomAction1** 项的快捷菜单，然后将其名称改为 **MyCustomAction**。  
  
     **“输出”**窗口中将显示确认信息.  此消息由 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> 事件处理程序编写, 此事件处理程序在你定义的 `CustomActionProjectItemTypeProvider` 类中。  当开发人员修改项目项时，您可以处理此事件和其他项目项事件以实现自定义行为。  
  
#### 测试 SharePoint 中的自定义操作  
  
1.  在 Visual Studio 的实验实例中，打开 Elements.xml 文件（此文件是**“MyCustomAction”**项目项的子级）。  
  
2.  在 Elements.xml 文件，请进行以下更改，然后保存文件：  
  
    -   在 `CustomAction` 元素中，将 `Id` 属性设置为 GUID 或某个其他唯一字符串，如下面的示例所示：  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   在 `CustomAction` 元素中，将 `Title` 属性设置为下例所示：  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   在 `CustomAction` 元素中，将 `Description` 属性设置为下例所示：  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   在 `UrlAction` 元素中，将 `Url` 属性设置为下例所示：  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  选择 F5 键。  
  
     这将对自定义操作进行打包并将其部署到由项目的**“网站 URL”**属性指定的 SharePoint 网站中。  Web 浏览器将打开此网站的默认页。  
  
    > [!NOTE]  
    >  如果出现**“脚本调试被禁用”**对话框，请单击**“是”**继续调试该项目。  
  
4.  在 **网站操作** 菜单中，选择 **SharePoint 开发中心**，验证浏览器中打开网站 http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx，然后关闭该浏览器。  
  
## 清理开发计算机  
 测试完项目项之后，从 Visual Studio 的实验实例中移除项目项模板。  
  
#### 清理开发计算机  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上选择 **“工具”**，**“扩展管理器”**。  
  
     “扩展和更新”对话框将打开。  
  
2.  在扩展列表中，单击**“自定义操作项目项”**，然后单击**“卸载”**。  
  
3.  在出现的对话框中，单击**“是”**以确认您要卸载该扩展。  
  
4.  选择 **立即重新启动** 按钮来完成卸载。  
  
5.  关闭 Visual Studio 的两个实例以及 CustomActionProjectItem 解决方案中已打开的实例。  
  
## 后续步骤  
 完成本演练后，可以向项模板添加向导。  当用户向 SharePoint 项目添加“自定义操作”项目项时，此向导将收集有关自定义操作的信息（如自定义操作的位置和自定义操作被选中时将导航到的 URL），并将此信息添加到新项目项的 Elements.xml 文件中。  有关详细信息，请参阅[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
## 请参阅  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  