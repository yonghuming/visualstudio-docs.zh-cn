---
title: "Walkthrough: Creating a SharePoint Project Extension"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  本演练阐释如何创建 SharePoint 项目的扩展。  向项目中添加，删除或重命名时，可以使用项目扩展响应项目级别事件 \(例如\)。  还可以添加自定义属性或在某个属性值更改时做出响应。  与项目项扩展不同，无法将项目扩展与特定的 SharePoint 项目类型相关联。  创建项目扩展后，当在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中打开任何类型的 SharePoint 项目时，此扩展都会加载。  
  
 在本演练中，您将创建一个将添加到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建的任何 SharePoint 项目中的自定义布尔属性。  如果设置为 **True**，则新属性会将 Images 资源文件夹添加或映射到您的项目。  如果设置为 **False**，则将删除 Images 文件夹（如果存在）。  有关更多信息，请参见[如何：添加和移除映射文件夹](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
 本演练将演示以下任务：  
  
-   为 SharePoint 项目创建可执行以下操作的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展：  
  
    -   将自定义项目属性添加到“属性”窗口。  该属性将应用于任何 SharePoint 项目。  
  
    -   使用 SharePoint 项目对象模型将映射文件夹添加到项目中。  
  
    -   使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 自动化对象模型 \(DTE\) 从项目中删除映射文件夹。  
  
-   生成 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展 \(VSIX\) 包以部署项目属性的扩展程序集。  
  
-   调试并测试项目属性。  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]、SharePoint 和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  本演练使用 [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目属性扩展。  有关更多信息，请参见[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
## 创建项目  
 若要完成本演练，您必须创建以下两个项目：  
  
-   一个用于创建 VSIX 包以部署项目扩展的 VSIX 项目。  
  
-   一个用于实现项目扩展的类库项目。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **扩展性** 节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio SDK，此节点可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
4.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**，然后选择 **VSIX 项目** 模板。  
  
5.  在 **名称** 框中，输入 **ProjectExtensionPackage**，然后选择 **确定** 按钮。  
  
     **ProjectExtensionPackage** 项显示在 **解决方案资源管理器**。  
  
#### 创建扩展项目  
  
1.  在 **解决方案资源管理器**，请打开解决方案节点的快捷菜单上，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 项目，因此，只有当 **总是显示解决方案** 复选框。[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)，已选择解决方案节点显示在 **解决方案资源管理器**。  
  
2.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **Windows**。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**，然后选择 **类库** 项目模板。  
  
4.  在 **名称** 框中，输入 **ProjectExtension**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“ProjectExtension”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置项目  
 在编写代码以创建项目扩展之前，请将代码文件和程序集引用添加到扩展项目中。  
  
#### 配置项目  
  
1.  添加一个名为" ProjectExtension 项目的 **CustomProperty** 的代码文件。  
  
2.  打开 **ProjectExtension** 项目的快捷菜单，然后选择 **添加引用**。  
  
3.  在 **引用管理器– CustomProperty** 对话框中，选择 **框架** 节点，请在 System.ComponentModel.Composition 和 System.Windows.Forms 程序集例旁边的复选框。  
  
4.  选择 **扩展** 节点，请在 Microsoft.VisualStudio.SharePoint 和 EnvDTE 程序集旁边的复选框，然后选择 **确定** 按钮。  
  
5.  在 **解决方案资源管理器**，在 **ProjectExtension** 项目的 **引用** 文件夹下，选择 **EnvDTE**。  
  
6.  在**“属性”**窗口中，将**“嵌入互操作类型”**属性更改为**“False”**。  
  
## 定义新的 SharePoint 项目属性  
 创建一个定义项目扩展和新项目属性的行为的类。  若要定义新的项目扩展，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 接口。  每当需要定义 SharePoint 项目扩展时，就要实现此接口。  另外，将 <xref:System.ComponentModel.Composition.ExportAttribute> 添加到此类中。  此特性使 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 能够发现和加载您的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 实现。  将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 类型传递给特性的构造函数。  
  
#### 定义新的 SharePoint 项目属性  
  
1.  将下面的代码粘贴到 CustomProperty 代码文件。  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## 生成解决方案  
 接下来，生成解决方案以确保编译时不会出错。  
  
#### 生成解决方案  
  
1.  在菜单栏上，依次选择 **Build**，**生成解决方案**。  
  
## 创建 VSIX 包以部署项目属性扩展  
 若要部署项目扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后，通过生成解决方案来创建 VSIX 包。  
  
#### 配置并创建 VSIX 包  
  
1.  在 **解决方案资源管理器**，打开 source.extension.vsixmanifest 文件的快捷菜单，然后选择 **打开** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 打开在清单设计器中的文件。  也会出现在 **元数据** 选项的信息显示在 **扩展和更新**。所有 VSIX 包必需的 extension.vsixmanifest 文件。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **产品名称** 框中，输入 **自定义项目属性**。  
  
3.  在 **作者** 框中，输入 **Contoso**。  
  
4.  在 **说明** 框中，输入 **切换映射 images 资源文件夹添加到项目中的自定义 SharePoint 项目属性**。  
  
5.  选择 **资产** 选项卡，然后选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
6.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MEFComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关更多信息，请参见[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目** 选项按钮。  
  
8.  在 **项目** 列表中，选择 **ProjectExtension**。  
  
     此值标识程序集的名称在项目中生成。  
  
9. 选择 **确定** 关闭 **添加新资产** 对话框。  
  
10. 在菜单栏上，依次选择 **文件**，**全部保存**，完成后，然后关闭清单设计器。  
  
11. 在菜单栏上，依次选择 **Build**，**生成解决方案**，然后确保项目在编译时不会出错。  
  
12. 在 **解决方案资源管理器**，打开 **ProjectExtensionPackage** 项目的快捷菜单，并选择 **在文件资源管理器中打开文件夹** 按钮。  
  
13. 在 **文件资源管理器**，请打开 ProjectExtensionPackage 项目的生成输出文件夹，然后验证该文件夹包含名为 ProjectExtensionPackage.vsix 的文件。  
  
     默认情况下，生成输出文件夹为  包含项目文件的文件夹下的 ..\\bin\\Debug 文件夹。  
  
## 测试项目属性  
 现在已准备好测试自定义项目属性。  调试和测试在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的实验实例的新项目属性扩展最为简单。  当您运行 VSIX 或其他扩展性项目时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 此创建实例。  在调试项目后，您的系统上安装该扩展然后继续调试和测试它在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]常规实例。  
  
#### 在 Visual Studio 的实验实例中调试和测试扩展  
  
1.  重新启动使用管理凭据的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后打开 ProjectExtensionPackage 解决方案。  
  
2.  通过选择 **F5** 键启动项目的调试版本或，在菜单栏上，选择 **调试**，**启动调试**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将扩展安装到 %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ custom project property \\ 1.0 中启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的实验实例。  
  
3.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的实验实例中，创建场解决方案的 SharePoint 项目，并为其他值使用默认值在向导。  
  
    1.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
    2.  在 **新建项目** 对话框的顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 3.5**。  
  
         SharePoint 工具扩展需要在 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]的这一版本的功能。  
  
    3.  在 **模板** 节点下，展开 **visual C\#** 或 **Visual Basic** 节点，选择 **SharePoint** 节点，然后选择 **2010** 节点。  
  
    4.  选择 **SharePoint 2010 项目** 模板，然后转到 **ModuleTest** 是项目的名称。  
  
4.  在 **解决方案资源管理器**，选择 **ModuleTest** 项目节点。  
  
     **“属性”**窗口中将显示新的自定义属性**“映射 Images 文件夹”**，其默认值为 **False**。  
  
5.  更改该属性的值更改为 **True**。  
  
     Images 资源文件夹将添加到 SharePoint 项目中。  
  
6.  更改该属性的值重 **False**。  
  
     如果选择在 **删除 images 文件夹？** 对话框的 **是** 按钮，images 资源文件夹从 SharePoint 项目中删除。  
  
7.  关闭 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的实验实例。  
  
## 请参阅  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  