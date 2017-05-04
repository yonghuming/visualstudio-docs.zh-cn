---
title: "Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  在 Visual Studio 中，可以使用 **服务器资源管理器SharePoint 连接** 节点来查看 SharePoint 网站的组件。  默认情况下，每隔 **服务器资源管理器** 不显示某些元素。  在本演练中，将扩展 **服务器资源管理器**，以使其显示在每个连接的 SharePoint 网站的 Web 部件库。  
  
 本演练将演示以下任务：  
  
-   创建一个 Visual Studio 扩展，此扩展可通过下列方式扩展**“服务器资源管理器”**：  
  
    -   该扩展添加一个 **Web 部件库** 节点在 **服务器资源管理器**的每个 SharePoint 网站节点下。  该新节点包含的每个子节点均表示网站上的 Web 部件库中的一个 Web 部件。  
  
    -   扩展定义表示 Web 部件实例新的节点。  该新节点类型是新**“Web 部件库”**节点下的子节点的基础。  该新 Web 部件节点类型在**“属性”**窗口中显示有关其表示的 Web 部件的信息。  节点类型还包括可以使用的自定义快捷菜单项，以用作执行与 Web 部件相关的其他任务的起点。  
  
-   创建扩展程序集调用的两个自定义 SharePoint 命令。  SharePoint 命令是在服务器对象模型可由扩展程序集调用使用 API 为 SharePoint 的方法。  在本演练中，您可以创建一些命令，这些命令会从开发计算机上的本地 SharePoint 网站中检索 Web 部件信息。  有关更多信息，请参见[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   生成 Visual Studio 扩展 \(VSIX\) 包以部署扩展。  
  
-   调试并测试扩展。  
  
> [!NOTE]  
>  有关使用 SharePoint 客户端对象模型而不是其服务器对象模型本演练的替代版本，请参见 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)。  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   Windows、SharePoint 和 Visual Studio 的支持的版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关更多信息，请参见[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   使用的 SharePoint 服务器对象模型。  有关更多信息，请参见 [Using the SharePoint Foundation Server\-Side Object Model](http://go.microsoft.com/fwlink/?LinkId=177796)（使用 SharePoint Foundation Server 端对象模型）。  
  
-   SharePoint 解决方案中的 Web 部件。  有关更多信息，请参见 [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803)（Web 部件概述）。  
  
## 创建项目  
 若要完成本演练，您必须创建三项：  
  
-   一个用于创建 VSIX 包以部署扩展的 VSIX 项目。  
  
-   一个用于实现扩展的类库项目。  此项目必须面向 .NET Framework 4.5。  
  
-   一个用于定义自定义 SharePoint 命令的类库项目。  此项目必须面向 .NET Framework 3.5。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在  **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **扩展性** 节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio SDK，**扩展性** 节点可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
4.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
5.  选择 **VSIX 项目** 模板，将项目命名为 **WebPartNode**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“WebPartNode”**项目添加到**“解决方案资源管理器”**中。  
  
#### 创建扩展项目  
  
1.  在 **解决方案资源管理器**，请打开解决方案节点的快捷菜单上，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在 **新建项目** 对话框中，展开 **visual C\#** 节点或 **Visual Basic** 节点，然后选择 **Windows** 节点。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
4.  在项目模板列表中，选择 **类库**，将项目命名为 **WebPartNodeExtension**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“WebPartNodeExtension”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
#### 创建 SharePoint 命令项目  
  
1.  在 **解决方案资源管理器**，请打开解决方案节点的快捷菜单上，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在  **新建项目** 对话框中，展开 **visual C\#** 节点或 **Visual Basic** 节点，然后选择 **Windows** 节点。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 3.5**。  
  
4.  在项目模板列表中，选择 **类库**，将项目命名为 **WebPartCommands**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“WebPartCommands”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置项目  
 在创建扩展编写代码，您必须先添加代码文件和程序集引用，并配置项目设置。  
  
#### 配置 WebPartNodeExtension 项目  
  
1.  在 WebPartNodeExtension 项目中，添加四个具有下列名称的代码文件：  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  打开 **WebPartNodeExtension** 项目的快捷菜单，然后选择 **添加引用**。  
  
3.  在 **引用管理器– WebPartNodeExtension** 对话框中，选择 **框架** 选项，以下程序集中的每个然后选中复选框：  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  选择 **扩展** 选项，为 Microsoft.VisualStudio.SharePoint 程序集的复选框，然后选择 **确定** 按钮。  
  
5.  在 **解决方案资源管理器**，打开 **WebPartNodeExtension** 项目节点的快捷菜单，然后选择 **属性**。  
  
     随即打开**“项目设计器”**。  
  
6.  选择 **应用程序** 选项。  
  
7.  在 **默认命名空间** 框 \(C\#\) 或 **根命名空间** 框 \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\)，输入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
#### 配置 WebPartCommands 项目  
  
1.  在 WebPartCommands 项目中，添加名为 WebPartCommands 的代码文件。  
  
2.  在 **解决方案资源管理器**，打开 **WebPartCommands** 项目节点的快捷菜单，选择 **添加**，然后选择 **现有项**。  
  
3.  在 **添加现有项** 对话框中，浏览到包含 WebPartNodeExtension 项目的代码文件的文件夹，然后选择 WebPartNodeInfo 和 WebPartCommandIds 代码文件。  
  
4.  在 **添加** 按钮旁边的下箭头，然后在出现的菜单中的 **添加为链接**。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将代码文件作为链接添加到 WebPartCommands 项目中。  因此，代码文件位于 WebPartNodeExtension 项目中，但文件中的代码还是在 WebPartCommands 项目中进行编译。  
  
5.  再次打开 **WebPartCommands** 项目的快捷菜单，并选择 **添加引用**。  
  
6.  在 **引用管理器– WebPartCommands** 对话框中，选择 **扩展** 选项，以下程序集中的每个复选框，然后选择 **确定** 按钮：  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  在 **解决方案资源管理器**，请再次打开 **WebPartCommands** 项目的快捷菜单，然后选择 **属性**。  
  
     随即打开**“项目设计器”**。  
  
8.  选择 **应用程序** 选项。  
  
9. 在 **默认命名空间** 框 \(C\#\) 或 **根命名空间** 框 \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\)，输入 **ServerExplorer.SharePointConnections.WebPartNode**。  
  
## 为新节点创建图标  
 为**“服务器资源管理器”**扩展创建两个图标：一个图标用于新的**“Web 部件库”**节点，另一个图标用于**“Web 部件库”**节点下的每个子 Web 部件节点。  在本演练后面的部分中，您将编写代码以将这些图标与节点相关联。  
  
#### 为节点创建图标  
  
1.  在 **解决方案资源管理器**，打开 **WebPartNodeExtension** 项目的快捷菜单，然后选择 **属性**。  
  
2.  随即打开**“项目设计器”**。  
  
3.  选择**资源**选项卡，然后选择该**此项目中不包含默认资源文件。单击此处创建** 链接。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建一个资源文件并在设计器中打开该文件。  
  
4.  在设计器的顶部，请在 **添加资源** 菜单命令旁边的下箭头，然后在出现的菜单中的 **添加新图标**。  
  
5.  在 **添加新资源** 对话框，则为新图标 **WebPartsNode**，然后选择 **添加** 按钮。  
  
     新图标将在**“图像编辑器”**中打开。  
  
6.  编辑 16x16 版本的图标，使其具有您可以轻松地识别的设计。  
  
7.  打开 32x32 版本的快捷菜单，然后选择 **删除图像类型**。  
  
8.  重复添加第二个图标的第 5 步到第 8 步到项目资源，并将此图标 **WebPart**。  
  
9. 在 **解决方案资源管理器**，在 **WebPartNodeExtension** 项目的 **资源** 文件夹下，打开 **WebPartsNode.ico**的快捷菜单。  
  
10. 在 **属性** 窗口，请在 **生成操作**旁边的下箭头，然后在出现的菜单中的 **嵌入的资源**。  
  
11. 对于**“WebPart.ico”**，重复最后两个步骤。  
  
## 向服务器资源管理器中添加 Web 部件库节点  
 创建一个类，此类可将新的**“Web 部件库”**节点添加到每个 SharePoint 网站节点中。  若要添加新节点，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 接口。  时，就要实现此接口来扩展现有节点的行为。**服务器资源管理器**\(例如，添加子节点为节点。  
  
#### 向服务器资源管理器中添加 Web 部件库节点  
  
1.  在 WebPartNodeExtension 项目中，打开 SiteNodeExtension 代码文件，然后将下面的代码粘贴到它。  
  
    > [!NOTE]  
    >  在添加此代码后，项目将会出现一些编译错误，但是，它们将消失，当您将在后面的步骤中代码。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## 定义表示 Web 部件的节点类型  
 创建一个类，此类定义表示 Web 部件的新节点类型。  Visual Studio 使用此新节点类型来显示节点下的子节点。**Web 部件库**。  每个子节点表示 SharePoint 网站的 Web 部件。  
  
 若要定义新节点类型，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 接口。  每当需要在**“服务器资源管理器”**中定义新的节点类型时，就要实现此接口。  
  
#### 定义 Web 部件节点类型  
  
1.  在 WebPartNodeExtension 项目中，打开 WebPartNodeTypeProvder 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## 定义 Web 部件数据类  
 定义一个类，此类包含有关 SharePoint 网站上的单个 Web 部件的数据。  在本演练中，您将创建检索有关每个 Web 部件的数据在网站中将数据分配给此选件类实例的自定义 SharePoint 命令。  
  
#### 定义 Web 部件数据类  
  
1.  在 WebPartNodeExtension 项目中，打开 WebPartNodeInfo 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## 定义 SharePoint 命令的 ID  
 定义若干个标识自定义 SharePoint 命令的字符串。  您将在本演练后面的部分中实现这些命令。  
  
#### 定义命令 ID  
  
1.  在 WebPartNodeExtension 项目中，打开 WebPartCommandIds 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## 创建自定义 SharePoint 命令  
 创建调入 SharePoint 服务器对象模型的可以检索有关 Web 部件的数据在 SharePoint 网站的自定义命令。  每条命令均是应用了 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 的方法。  
  
#### 定义 SharePoint 命令  
  
1.  在 WebPartCommands 项目中，打开 WebPartCommands 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## 检查点  
 演练进行到此时，**“Web 部件库”**节点和 SharePoint 命令的所有代码现在都位于项目中。  生成解决方案以确保项目在编译时不会出错。  
  
#### 生成解决方案  
  
1.  在菜单栏上，依次选择 **Build**，**生成解决方案**。  
  
    > [!WARNING]  
    >  此时，因为 VSIX 清单文件没有作者的，一个值 WebPartNode 项目可能出现生成错误。  当您将在后面的步骤值时，此错误将消失。  
  
## 创建 VSIX 包以部署扩展  
 若要部署扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后，通过生成解决方案来创建 VSIX 包。  
  
#### 配置 VSIX 包  
  
1.  在 **解决方案资源管理器**，在 WebPartNode 项目中，打开在清单编辑器中 **source.extension.vsixmanifest** 文件。  
  
     source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **产品名称** 框中，输入 **Web 部件服务器资源管理器的库节点**。  
  
3.  在 **作者** 框中，输入 **Contoso**。  
  
4.  在**声明**框中，输入添加**自定义 Web 部件库节点到在服务器资源管理器中的“SharePoint 连接”节点。此扩展使用自定义 SharePoint 命令调入服务器对象模型。”**。  
  
5.  选择编辑器的 **资产** 选项卡，然后选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
6.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关更多信息，请参见[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
8.  在 **项目** 列表中，选择 **WebPartNodeExtension** 然后选择 **确定** 按钮。  
  
9. 在清单编辑器，请选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
10. 在 **类型** 框中，输入 **SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  此元素指定要包括在 Visual Studio 扩展中的自定义扩展。  有关更多信息，请参见[属性元素 \(VSX 架构\)](http://msdn.microsoft.com/zh-cn/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在 **源** 列表中，选择 **当前解决方案中的项目** 列表项。  
  
12. 在 **项目** 列表中，选择 **WebPartCommands**，然后选择 **确定** 按钮。  
  
13. 在菜单栏上，依次选择 **Build**，**生成解决方案**，然后确保解决方案已生成且未发生错误。  
  
14. 确保 WebPartNode 项目的生成输出文件夹现在包含 WebPartNode.vsix 文件。  
  
     默认情况下，生成输出文件夹为  包含项目文件的文件夹下的 ..\\bin\\Debug 文件夹。  
  
## 测试扩展  
 您现在可以测试在 **服务器资源管理器**的新 **Web 部件库** 节点。  首先，在 Visual Studio 的实验实例中开始调试扩展。  然后，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的实验实例中使用新的**“Web 部件”**节点。  
  
#### 开始调试扩展  
  
1.  重新启动使用管理凭据的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后打开 WebPartNode 解决方案。  
  
2.  在 WebPartNodeExtension 项目中，打开 SiteNodeExtension 代码文件，然后将断点添加到第一个代码行中 `NodeChildrenRequested` 和 `CreateWebPartNodes` 方法的。  
  
3.  选择 F5 键开始调试。  
  
     Visual Studio 将扩展安装到 %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ Web 部件库节点扩展服务器资源管理器\\ 1.0 中并启动 Visual Studio 的实验实例。  您将在此 Visual Studio 实例中测试项目项。  
  
#### 测试扩展  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的实验实例中，在菜单栏上，依次选择 **视图**，**服务器资源管理器**。  
  
2.  请执行以下步骤，如果要用于测试的 SharePoint 网站未出现在 **服务器资源管理器**的 **SharePoint 连接** 节点中：  
  
    1.  在 **服务器资源管理器**，打开 **SharePoint 连接**的快捷菜单，然后选择 **添加连接**。  
  
    2.  在 **添加 SharePoint 连接** 对话框中，输入要连接到的 SharePoint 网站的 URL，然后选择 **确定** 按钮。  
  
         若要指定开发计算机上的 SharePoint 网站，输入 **http:\/\/localhost**。  
  
3.  展开显示网站的 URL 的节点\) \(，然后展开子网站节点 \(例如，**团队网站**\)。  
  
4.  验证在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 另一个实例中的代码在 `NodeChildrenRequested` 方法设置的断点处停止，然后选择 F5 继续调试项目。  
  
5.  在 Visual Studio 的实验实例中，验证名为 **Web 部件库** 的新节点是否显示在首要网站节点下，再展开 **Web 部件库** 节点。  
  
6.  验证另一个 Visual Studio 实例的代码在 `CreateWebPartNodes` 方法设置的断点处停止，然后选择 F5 键继续调试项目。  
  
7.  在 Visual Studio 的实验实例中，验证已连接网站上的所有 Web 部件以显示在 **服务器资源管理器**的 **Web 部件库** 节点下。  
  
8.  在 **服务器资源管理器**，打开之一的快捷菜单 Web 部件，然后选择 **属性**。  
  
9. 在调试 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 实例中，验证有关 Web 部件的详细信息显示在 **属性** 窗口。  
  
## 从 Visual Studio 中卸载扩展  
 测试完扩展后，请从 Visual Studio 卸载扩展。  
  
#### 卸载扩展  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的实验实例中，在菜单栏上，依次选择 **工具**，**扩展和更新**。  
  
     **扩展和更新** 对话框打开。  
  
2.  在扩展列表中，选择 **Web 部件库服务器资源管理器的节点扩展**，然后选择 **卸载** 按钮。  
  
3.  在出现的对话框中，选择 **是** 按钮以确认您要卸载该扩展，然后选择 **立即重新启动** 按钮来卸载。  
  
4.  关闭 Visual Studio 的实验实例 \(和 WebPartNode 解决方案处于打开状态的实例\) 两个实例 Visual Studio。  
  
## 请参阅  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  