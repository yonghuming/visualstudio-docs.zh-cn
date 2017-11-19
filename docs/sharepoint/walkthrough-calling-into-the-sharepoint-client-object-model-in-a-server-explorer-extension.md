---
title: "演练： 调入 SharePoint 客户端对象模型在服务器资源管理器扩展 |Microsoft 文档"
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
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 489a11c215fe590b85e9dfaf5cbd815fdc43acb3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>演练：在服务器资源管理器扩展中调入 SharePoint 客户端对象模型
  本演练演示如何调用 SharePoint 客户端对象模型的扩展从**SharePoint 连接**中的节点**服务器资源管理器**。 有关如何使用 SharePoint 客户端对象模型的详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
 本演练演示了下列任务：  
  
-   创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展插件**SharePoint 连接**节点**服务器资源管理器**通过以下方式：  
  
    -   通过扩展添加**Web 部件库**中每个 SharePoint 站点节点下的节点**服务器资源管理器**。 这个新节点包含表示每个站点上的 Web 部件库中的 Web 部件的子节点。  
  
    -   扩展定义新类型的节点，它表示 Web 部件实例。 此新的节点类型是在新的子节点的基础**Web 部件库**节点。 新的 Web 部件节点类型显示在信息**属性**有关该节点表示的 Web 部件的窗口。  
  
-   生成 Visual Studio 扩展 (VSIX) 包以部署该扩展。  
  
-   调试和测试扩展。  
  
> [!NOTE]  
>  本演练中创建的扩展类似于在中创建的扩展[演练： 扩展服务器资源管理器显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。 该演练使用 SharePoint 服务器对象模型，但本演练通过使用客户端对象模型完成相同任务。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练的开发计算机上：  
  
-   受支持的 Windows、 SharePoint 和 Visual Studio 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本演练使用**VSIX 项目**创建 VSIX 包来部署该扩展 SDK 中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   使用 SharePoint 客户端对象模型。 有关详细信息，请参阅[托管客户端对象模型](http://go.microsoft.com/fwlink/?LinkId=177797)。  
  
-   在 SharePoint web 部件。 有关详细信息，请参阅[Web 部件概述](http://go.microsoft.com/fwlink/?LinkId=177803)。  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，必须创建两个项目：  
  
-   VSIX 项目创建 VSIX 包来部署**服务器资源管理器**扩展。  
  
-   一个类库项目实现**服务器资源管理器**扩展。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-vsix-project"></a>若要创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**扩展性**。  
  
    > [!NOTE]  
    >  **扩展性**节点是安装 Visual Studio SDK 时才可用。 有关详细信息，请参阅本主题前面的先决条件部分。  
  
4.  在对话框中的顶部，选择**.NET Framework 4.5**在列表中的.NET framework 的版本。  
  
     SharePoint 工具扩展需要在此版本的.NET Framework 的功能。  
  
5.  选择**VSIX 项目**模板。  
  
6.  在**名称**框中，键入**WebPartNode**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**WebPartNode**项目合并为**解决方案资源管理器**。  
  
#### <a name="to-create-the-extension-project"></a>若要创建扩展项目  
  
1.  在**解决方案资源管理器**，打开解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**Windows**。  
  
3.  在对话框中的顶部，选择**.NET Framework 4.5**在列表中的.NET framework 的版本。  
  
4.  在项目模板列表中，选择**类库**。  
  
5.  在**名称**框中，输入**WebPartNodeExtension**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**WebPartNodeExtension**到解决方案的项目并打开默认 Class1 代码文件。  
  
6.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-extension-project"></a>配置扩展项目  
 在编写代码以创建扩展之前，你必须添加代码文件和程序集引用到你的项目，并且您必须更新默认命名空间。  
  
#### <a name="to-configure-the-project"></a>若要配置项目  
  
1.  在**WebPartNodeExtension**项目中，添加两个分别名为 SiteNodeExtension 和 WebPartNodeTypeProvider 的代码文件。  
  
2.  打开 WebPartNodeExtension 项目的快捷菜单，然后选择**添加引用**。  
  
3.  在**引用管理器-WebPartNodeExtension**对话框框中，选择**Framework**节点，，然后选择对应的复选框 System.ComponentModel.Composition 和 System.Windows.Forms 的程序集。  
  
4.  选择**扩展**节点，每个以下程序集，选择复选框，然后选择**确定**按钮：  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  打开的快捷菜单**WebPartNodeExtension**项目，，然后选择**属性**。  
  
     将打开“项目设计器”。  
  
6.  选择“应用程序”选项卡。  
  
7.  在**默认命名空间**框 (C#) 或**根命名空间**框 (Visual Basic 中) 中，输入**ServerExplorer.SharePointConnections.WebPartNode**。  
  
## <a name="creating-icons-for-the-new-nodes"></a>为新的节点创建图标  
 创建两个图标**服务器资源管理器**扩展： 新的图标**Web 部件库**节点和每个子 Web 部件节点下的另一个图标**Web 部件库**节点。 稍后在本演练中，你将编写将这些图标与节点相关联的代码。  
  
#### <a name="to-create-icons-for-the-nodes"></a>若要创建的节点的图标  
  
1.  在**项目设计器**WebPartNodeExtension 项目中，选择**资源**选项卡。  
  
2.  选择链接**此项目不包含默认资源文件。单击此处创建一个资源文件。”**。  
  
     Visual Studio 创建的资源文件，并在设计器中打开它。  
  
3.  在设计器的顶部，选择箭头上**添加资源**菜单命令时，，然后选择**添加新图标**。  
  
4.  输入**WebPartsNode**新图标，则名称，然后选择**添加**按钮。  
  
     在新建图标打开**图像编辑器**。  
  
5.  编辑的图标 16 x 16 版本，以便它具有你可以轻松识别的设计。  
  
6.  打开的图标，32 x 32 版本的快捷菜单，然后选择**删除图像类型**。  
  
7.  重复步骤 3 至 7 将第二个图标添加到的项目资源，并命名为此图标**web 部件**。  
  
8.  在**解决方案资源管理器**中**资源**文件夹**WebPartNodeExtension**项目，选择**WebPartsNode.ico**。  
  
9. 在**属性**窗口中，打开**生成操作**列表，，然后选择**嵌入的资源**。  
  
10. 重复的最后两个步骤**WebPart.ico**。  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Web 部件库节点添加到服务器资源管理器  
 创建一个类，添加新**Web 部件库**到每个 SharePoint 站点节点的节点。 若要添加新节点，此类应实现<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>接口。 实现此接口，无论何时你想要扩展的行为中的现有节点的**服务器资源管理器**，例如添加新的子节点到节点。  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>若要将 Web 部件库节点添加到服务器资源管理器  
  
1.  粘贴下面的代码插入**SiteNodeExtension**代码文件**WebPartNodeExtension**项目。  
  
    > [!NOTE]  
    >  添加此代码后，项目将出现一些编译错误。 在后续步骤中添加代码，这些错误将会消失。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>定义表示 Web 部件的节点类型  
 创建用于定义一种表示 Web 部件的节点的新类。 Visual Studio 将使用此新的节点类型以显示下的子节点**Web 部件库**节点。 每个这些子节点表示 SharePoint 站点上的单个 Web 部件。  
  
 若要定义新的节点类型，此类应实现<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>接口。 每当你想要定义新类型的节点中实现此接口**服务器资源管理器**。  
  
#### <a name="to-define-the-web-part-node-type"></a>若要定义 Web 部件节点类型  
  
1.  粘贴下面的代码插入**WebPartNodeTypeProvider**代码文件**WebPartNodeExtension**项目。  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>检查点  
 在本演练中，所有的代码中这一时刻**Web 部件库**节点现已在该项目。 生成**WebPartNodeExtension**项目以确保它在编译时没有错误。  
  
#### <a name="to-build-the-project"></a>生成项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单**WebPartNodeExtension**项目，，然后选择**生成**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>创建 VSIX 包来部署扩展  
 若要部署的扩展，使用 VSIX 项目解决方案中创建 VSIX 包。 首先，通过修改项目中包含的 source.extension.vsixmanifest 文件中配置 VSIX 包。 通过生成解决方案，然后创建 VSIX 包。  
  
#### <a name="to-configure-the-vsix-package"></a>若要配置 VSIX 包  
  
1.  在**解决方案资源管理器**中**WebPartNode**项目中，打开**source.extension.vsixmanifest**在清单编辑器中的文件。  
  
     Source.extension.vsixmanifest 文件是所有的 VSIX 包需要 extension.vsixmanifest 文件的基础。 有关此文件的详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**产品名称**框中，输入**服务器资源管理器 Web 部件库节点**。  
  
3.  在**作者**框中，输入**Contoso**。  
  
4.  在**说明**框中，输入**将自定义 Web 部件库节点添加到服务器资源管理器中的 SharePoint 连接节点**。  
  
5.  上**资产**选项卡的编辑器中，选择**新建**按钮。  
  
6.  在**添加新资产**对话框中，在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于`MefComponent`extension.vsixmanifest 文件中的元素。 此元素指定的 VSIX 包中的扩展程序集的名称。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**源**列表中，选择**当前解决方案中的项目**。  
  
8.  在**项目**列表中，选择**WebPartNodeExtension**，然后选择**确定**按钮。  
  
9. 在菜单栏上，选择**生成**，**生成解决方案**，并确保解决方案在编译时没有错误。  
  
10. 请确保 WebPartNode 项目的生成输出文件夹现在包含 WebPartNode.vsix 文件。  
  
     默认情况下，生成输出文件夹是...在包含你的项目文件的文件夹下的 \bin\Debug 文件夹。  
  
## <a name="testing-the-extension"></a>测试扩展  
 你现在就可以测试新**Web 部件库**中的节点**服务器资源管理器**。 首先，开始调试 Visual Studio 的实验实例中的扩展项目。 然后使用新**Web 部件**Visual Studio 的实验实例中的节点。  
  
#### <a name="to-start-debugging-the-extension"></a>若要开始调试扩展  
  
1.  使用管理凭据，重新启动 Visual Studio，然后打开**WebPartNode**解决方案。  
  
2.  在 WebPartNodeExtension 项目中，打开**SiteNodeExtension**代码文件，然后将断点添加到代码中的第一个行`NodeChildrenRequested`和`CreateWebPartNodes`方法。  
  
3.  选择 F5 键开始调试。  
  
     Visual Studio 会为服务器 Explorer\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 部件库节点扩展到安装扩展，并启动 Visual Studio 的实验实例。 你将在 Visual Studio 的此实例中测试的项目项。  
  
#### <a name="to-test-the-extension"></a>若要测试此扩展  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**视图**，**服务器资源管理器**。  
  
2.  验证你想要用于测试的 SharePoint 站点显示在**SharePoint 连接**中的节点**服务器资源管理器**。 如果未列出，请按照下列步骤：  
  
    1.  打开的快捷菜单**SharePoint 连接**，然后选择**添加连接**。  
  
    2.  在**添加 SharePoint 连接**对话框框中，输入你想要连接，然后依次的 SharePoint 站点的 URL**确定**按钮。  
  
         若要指定 SharePoint 站点，你的开发计算机上，键入**http://localhost**。  
  
3.  站点连接节点 （其中显示你的站点的 URL），再展开一个子节点 (例如，**团队站点**)。  
  
4.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`NodeChildrenRequested`方法，然后选择 F5 键以继续调试项目。  
  
5.  在 Visual Studio 的实验实例中，展开**Web 部件库**节点，显示在顶层站点节点下。  
  
6.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`CreateWebPartNodes`方法，然后选择 F5 键以继续调试项目。  
  
7.  在 Visual Studio 的实验实例中，验证是否连接到的站点上的所有 Web 部件都显示下**Web 部件库**中的节点**服务器资源管理器**。  
  
8.  为 Web 部件中，打开快捷菜单，然后选择**属性**。  
  
9. 在**属性**窗口中，验证是否显示了有关 Web 部件的详细信息。  
  
10. 在**服务器资源管理器**，为同一个 Web 部件中，打开快捷菜单，然后选择**显示消息**。  
  
     在显示的消息框中，选择**确定**按钮。  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>从 Visual Studio 中卸载扩展  
 在完成测试扩展后，它从 Visual Studio 中卸载。  
  
#### <a name="to-uninstall-the-extension"></a>卸载扩展  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**服务器资源管理器 Web 部件库节点**，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**按钮。  
  
4.  选择**立即重新启动**按钮以完成卸载。  
  
     项目项也被卸载。  
  
5.  关闭 Visual Studio （实验实例和 WebPartNode 解决方案处于打开状态的 Visual Studio 的实例） 的两个实例。  
  
## <a name="see-also"></a>另请参阅  
 [调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [扩展服务器资源管理器中的 SharePoint 连接节点](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [演练： 扩展服务器资源管理器以显示 Web 部件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [图标的图像编辑器](/cpp/windows/image-editor-for-icons)   
 [一个图标或其他图像 &#40; 上的图像编辑器创建图标 &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  