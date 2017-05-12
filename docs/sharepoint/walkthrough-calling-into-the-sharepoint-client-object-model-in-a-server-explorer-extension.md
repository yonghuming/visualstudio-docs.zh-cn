---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  本演练演示如何从**“服务器资源管理器”**中的**“SharePoint 连接”**节点扩展调用 SharePoint 客户端对象模型。  有关如何使用 SharePoint 客户端对象模型的更多信息，请参见 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
 本演练将演示以下任务：  
  
-   创建一个 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 扩展，此扩展通过以下方式扩展**“服务器资源管理器”**的**“SharePoint 连接”**节点：  
  
    -   该扩展添加一个 **Web 部件库** 节点在 **服务器资源管理器**的每个 SharePoint 网站节点下。  该新节点包含的每个子节点均表示网站上的 Web 部件库中的一个 Web 部件。  
  
    -   扩展定义表示 Web 部件实例新的节点。  该新节点类型是新**“Web 部件库”**节点下的子节点的基础。  该新 Web 部件节点类型显示在 **属性** 窗口中有关该节点表示的 Web 部件。  
  
-   生成 Visual Studio 扩展 \(VSIX\) 包以部署扩展。  
  
-   调试并测试扩展。  
  
> [!NOTE]  
>  在本演练中创建的扩展类似于您在 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)创建的扩展。  本演练使用 SharePoint 服务器对象模型，但是，本演练通过使用客户端对象模型，来完成相同的任务。  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   Windows、SharePoint 和 Visual Studio 的支持的版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本演练使用此 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署扩展。  有关更多信息，请参见[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   使用 SharePoint 客户端对象模型。  有关更多信息，请参见 [Managed Client Object Model](http://go.microsoft.com/fwlink/?LinkId=177797)（托管客户端对象模型）。  
  
-   在 SharePoint 的 Web 部件。  有关更多信息，请参见 [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803)（Web 部件概述）。  
  
## 创建项目  
 若要完成本演练，您必须创建以下两个项目：  
  
-   VSIX 项目创建 VSIX包以部署**“服务器资源管理器”**扩展。  
  
-   实现**“服务器资源管理器”**扩展的类库项目。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **扩展性**。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio SDK，**扩展性** 节点可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
4.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
     SharePoint 工具扩展需要在 .NET Framework 的这一版本的功能。  
  
5.  选择 **VSIX 项目** 模板。  
  
6.  在 **名称** 框中，键入 **WebPartNode**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“WebPartNode”**项目添加到**“解决方案资源管理器”**中。  
  
#### 创建扩展项目  
  
1.  在 **解决方案资源管理器**，请打开解决方案节点的快捷菜单上，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在  **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **Windows**。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
4.  在项目模板列表中，选择 **类库**。  
  
5.  在 **名称** 框中，输入 **WebPartNodeExtension**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“WebPartNodeExtension”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
6.  从项目中删除 Class1 代码文件。  
  
## 配置扩展项目  
 在创建扩展编写代码，您必须先添加代码文件和程序集引用添加到项目，因此，您必须更新默认命名空间。  
  
#### 配置项目  
  
1.  在 **WebPartNodeExtension** 项目中，添加名为 SiteNodeExtension 和 WebPartNodeTypeProvider 的两个代码文件。  
  
2.  打开 WebPartNodeExtension 项目的快捷菜单，然后选择 **添加引用**。  
  
3.  在 **引用管理器– WebPartNodeExtension** 对话框中，选择 **框架** 节点，为 System.ComponentModel.Composition 和 System.Windows.Forms 程序集的然后选中复选框。  
  
4.  选择 **扩展** 节点，以下程序集中的每个复选框，然后选择 **确定** 按钮：  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  打开 **WebPartNodeExtension** 项目的快捷菜单，然后选择 **属性**。  
  
     随即打开**“项目设计器”**。  
  
6.  选择 **应用程序** 选项。  
  
7.  在 **默认命名空间** 框 \(C\#\) 或 **根命名空间** 框 \(Visual Basic\) 中，输入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
## 为新节点创建图标  
 创建 **服务器资源管理器** 扩展的两个图标：新 **Web 部件库** 节点的图标和每个子 Web 的另一个图标部件节点。**Web 部件库** 节点下。  在本演练中，您将关联这些图标与节点的代码。  
  
#### 为节点创建图标  
  
1.  在 WebPartNodeExtension 项目的 **项目设计器**，选择 **资源** 选项。  
  
2.  选择 **此项目中不包含默认资源文件链接。单击此处创建一个资源文件。”**。  
  
     Visual Studio 会创建一个资源文件并在设计器中打开该文件。  
  
3.  在设计器的顶部，选择。**添加资源** 菜单命令的箭头，然后选择 **添加新图标**。  
  
4.  新图标名称的 Enter **WebPartsNode**，然后选择 **添加** 按钮。  
  
     新图标将在**“图像编辑器”**中打开。  
  
5.  编辑 16x16 版本的图标，使其具有您可以轻松地识别的设计。  
  
6.  打开 32x32 版本的快捷菜单，然后选择 **删除图像类型**。  
  
7.  重复添加第二个图标的第 3 步到第 7 步到项目资源，并将此图标 **WebPart**。  
  
8.  在 **解决方案资源管理器**，在 **WebPartNodeExtension** 项目的 **资源** 文件夹，选择 **WebPartsNode.ico**。  
  
9. 在 **属性** 窗口中，打开 **生成操作** 列表，然后选择 **嵌入的资源**。  
  
10. 对于**“WebPart.ico”**，重复最后两个步骤。  
  
## 向服务器资源管理器中添加 Web 部件库节点  
 创建一个类，此类可将新的**“Web 部件库”**节点添加到每个 SharePoint 网站节点中。  若要添加新节点，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口。  每当需要扩展**“服务器资源管理器”**中的现有节点的行为（例如向某个节点添加新的子节点）时，就要实现此接口。  
  
#### 向服务器资源管理器中添加 Web 部件库节点  
  
1.  将下面的代码粘贴到 **WebPartNodeExtension** 项目的 **SiteNodeExtension** 代码文件。  
  
    > [!NOTE]  
    >  在添加此代码后，项目将会出现一些编译错误。  在添加后面的步骤中的代码之后，这些错误将消失。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## 定义表示 Web 部件的节点类型  
 创建一个类，此类定义表示 Web 部件的新节点类型。  Visual Studio 使用此新节点类型来显示节点下的子节点。**Web 部件库**。  其中的每个子节点均表示 SharePoint 网站上的一个 Web 部件。  
  
 若要定义新节点类型，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 接口。  每当需要在**“服务器资源管理器”**中定义新的节点类型时，就要实现此接口。  
  
#### 定义 Web 部件节点类型  
  
1.  将下面的代码粘贴到 **WebPartNodeExtension** 项目的 **WebPartNodeTypeProvider** 代码文件。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## 检查点  
 演练进行到此时，**“Web 部件库”**节点的所有代码都位于项目中。  生成 **WebPartNodeExtension** 项目，以确保它在编译时不会出错。  
  
#### 生成项目  
  
1.  在 **解决方案资源管理器**，打开 **WebPartNodeExtension** 项目的快捷菜单，然后选择 **Build**。  
  
## 创建 VSIX 包以部署扩展  
 若要部署扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改项目中包含的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后通过生成解决方案创建 VSIX 包。  
  
#### 配置 VSIX 包  
  
1.  在 **解决方案资源管理器**，在 **WebPartNode** 项目中，打开在清单编辑器中 **source.extension.vsixmanifest** 文件。  
  
     source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **产品名称** 框中，输入 **Web 部件服务器资源管理器的库节点**。  
  
3.  在 **作者** 框中，输入 **Contoso**。  
  
4.  在 **说明** 框中，输入 **添加自定义 Web 部件库节点到在服务器资源管理器中的" SharePoint 连接"节点**。  
  
5.  在编辑器中 **资产** 选项卡中，选择 **新建** 按钮。  
  
6.  在 **添加新资产** 对话框中，在 **类型** 列表中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关更多信息，请参见[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
8.  在 **项目** 列表中，选择 **WebPartNodeExtension**，然后选择 **确定** 按钮。  
  
9. 在菜单栏上，依次选择 **Build**，**生成解决方案**，然后确保解决方案已生成且未发生错误。  
  
10. 确保 WebPartNode 项目的生成输出文件夹现在包含 WebPartNode.vsix 文件。  
  
     默认情况下，生成输出文件夹为  包含项目文件的文件夹下的 ..\\bin\\Debug 文件夹。  
  
## 测试扩展  
 此时，您可以对**“服务器资源管理器”**中的新**“Web 部件库”**节点进行测试。  首先，调试在 Visual Studio 的实验实例中扩展项目的开头。  然后使用新的 **Web 部件** 节点在 Visual Studio 的实验实例。  
  
#### 开始调试扩展  
  
1.  重新启动使用管理凭据的 Visual Studio，然后打开 **WebPartNode** 解决方案。  
  
2.  在 WebPartNodeExtension 项目中，打开 **SiteNodeExtension** 代码文件，然后将断点添加到第一个代码行中 `NodeChildrenRequested` 和 `CreateWebPartNodes` 方法的。  
  
3.  选择 F5 键开始调试。  
  
     Visual Studio 将扩展安装到 %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ Web 部件库节点扩展服务器资源管理器\\ 1.0 中并启动 Visual Studio 的实验实例。  在此 Visual Studio 实例中测试项目项。  
  
#### 测试扩展  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **视图**，**服务器资源管理器**。  
  
2.  验证要用于测试的 SharePoint 网站是否显示在**“服务器资源管理器”**中的**“SharePoint 连接”**节点下。  如果未列出，请执行以下步骤：  
  
    1.  打开 **SharePoint 连接**的快捷菜单，然后选择 **添加连接**。  
  
    2.  在 **添加 SharePoint 连接** 对话框中，输入要连接到的 SharePoint 网站的 URL，然后选择 **确定** 按钮。  
  
         若要指定开发计算机上的 SharePoint 网站，请键入 **http:\/\/localhost**。  
  
3.  展开显示网站的 URL 的节点\) \(，然后展开子网站节点 \(例如，**团队网站**\)。  
  
4.  验证另一个 Visual Studio 实例的代码在 `NodeChildrenRequested` 方法设置的断点处停止，然后选择 F5 键继续调试项目。  
  
5.  在 Visual Studio 的实验实例中，展开 **Web 部件库** 节点，该节点显示在首要网站节点下。  
  
6.  验证另一个 Visual Studio 实例的代码在 `CreateWebPartNodes` 方法设置的断点处停止，然后选择 F5 键继续调试项目。  
  
7.  在 Visual Studio 的实验实例中，验证已连接网站上的所有 Web 部件是否都显示在**“服务器资源管理器”**中的**“Web 部件库”**节点下。  
  
8.  打开 Web 部件的快捷菜单，然后选择 **属性**。  
  
9. 在 **属性** 窗口，请验证有关 Web 部件的详细信息显示。  
  
10. 在 **服务器资源管理器**，打开同一个 Web 部件的快捷菜单，然后选择 **显示消息**。  
  
     在出现的消息框中，选择 **确定** 按钮。  
  
## 从 Visual Studio 中卸载扩展  
 测试完扩展后，请将其卸载从 Visual Studio。  
  
#### 卸载扩展  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **工具**，**扩展和更新**。  
  
     **扩展和更新** 对话框打开。  
  
2.  在扩展列表中，选择 **Web 部件服务器资源管理器的库节点**，然后选择 **卸载** 按钮。  
  
3.  在出现的对话框中，选择 **是** 按钮。  
  
4.  选择 **立即重新启动** 按钮来卸载。  
  
     相应的项目项也会随之卸载。  
  
5.  关闭 Visual Studio 的实验实例 \(和 WebPartNode 解决方案处于打开状态的实例\) 两个实例 Visual Studio。  
  
## 请参阅  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  