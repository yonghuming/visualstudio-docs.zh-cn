---
title: "演练： 扩展 SharePoint 项目项类型 |Microsoft 文档"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8afe8ed1d59f8daec34a99b1479079a69a1bc740
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>演练：扩展 SharePoint 项目项类型
  你可以使用**业务数据连接模型**用于在 SharePoint 中创建业务数据连接 (BDC) 服务的型号项目项。 默认情况下，通过使用此项目项，创建模型时模型中的数据是不向用户显示。 你还必须在 SharePoint，以使用户能够查看数据中创建外部列表。  
  
 在本演练中，你将创建的扩展**业务数据连接模型**项目项。 开发人员可以使用扩展其 BDC 模型中显示的数据的项目中创建外部列表。 本演练演示了下列任务：  
  
-   创建一个 Visual Studio 扩展来执行两项主要任务：  
  
    -   它会生成 BDC 模型中显示的数据的外部列表。 扩展使用 SharePoint 项目系统的对象的模型来生成一个 Elements.xml 文件，它定义的列表。 它还将文件添加到项目，以便它与 BDC 模型一起部署。  
  
    -   它将添加到快捷菜单项**业务数据连接模型**项目中的项**解决方案资源管理器**。 开发人员可以单击此菜单项以生成 BDC 模型的外部列表。  
  
-   生成 Visual Studio 扩展 (VSIX) 包以部署扩展程序集。  
  
-   测试扩展。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练的开发计算机上：  
  
-   受支持的 Microsoft Windows、 SharePoint 和 Visual Studio 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本演练使用**VSIX 项目**SDK 创建 VSIX 包来部署项目项中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   中的 BDC 服务[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。 有关详细信息，请参阅[BDC 体系结构](http://go.microsoft.com/fwlink/?LinkId=177798)。  
  
-   BDC 模型的 XML 架构。 有关详细信息，请参阅[BDC 模型基础结构](http://go.microsoft.com/fwlink/?LinkId=177799)。  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，你需要创建两个项目：  
  
-   若要创建 VSIX 包来部署项目项扩展一个 VSIX 项目。  
  
-   一个用于实现项目项扩展的库项目。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-vsix-project"></a>若要创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**扩展性**节点。  
  
    > [!NOTE]  
    >  **扩展性**节点是安装 Visual Studio SDK 时才可用。 有关详细信息，请参阅本主题前面的先决条件部分。  
  
4.  在顶部列表中**新项目**对话框框中，选择**.NET Framework 4.5**。  
  
     SharePoint 工具扩展需要在此版本的.NET Framework 的功能。  
  
5.  选择**VSIX 项目**模板。  
  
6.  在**名称**框中，输入**GenerateExternalDataLists**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**GenerateExternalDataLists**项目合并为**解决方案资源管理器**。  
  
7.  如果未自动打开 source.extension.vsixmanifest 文件中，在 GenerateExternalDataLists 项目中，打开其快捷菜单，然后选择**打开**  
  
8.  验证 source.extension.vsixmanifest 文件中具有非空条目 （输入 Contoso） 的创作字段中，保存该文件，并将然后将其关闭。  
  
#### <a name="to-create-the-extension-project"></a>若要创建扩展项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单**GenerateExternalDataLists**解决方案节点，选择**添加**，然后选择**新项目**.  
  
2.  在**添加新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**Windows**节点。  
  
3.  在对话框顶部列表中，选择**.NET Framework 4.5**。  
  
4.  在项目模板列表中，选择**类库**。  
  
5.  在**名称**框中，输入**BdcProjectItemExtension**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**BdcProjectItemExtension**到解决方案的项目并打开默认 Class1 代码文件。  
  
6.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-extension-project"></a>配置扩展项目  
 在编写代码以创建项目项扩展之前，添加代码文件和向扩展项目的程序集引用。  
  
#### <a name="to-configure-the-project"></a>若要配置项目  
  
1.  在 BdcProjectItemExtension 项目中，添加具有以下名称的两个代码文件：  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  选择 BdcProjectItemExtension 项目，然后，在菜单栏上，选择**项目**，**添加引用**。  
  
3.  下**程序集**节点，选择**Framework**节点，然后选择复选框为每个以下程序集：  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  下**程序集**节点，选择**扩展**节点，，然后选择复选框为以下程序集：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  选择“确定”  按钮。  
  
## <a name="defining-the-project-item-extension"></a>定义项目项扩展  
 创建定义的扩展的类**业务数据连接模型**项目项。 若要定义扩展，此类应实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>接口。 无论何时你想要扩展现有类型的项目项，则实现此接口。  
  
#### <a name="to-define-the-project-item-extension"></a>若要定义项目项扩展  
  
1.  粘贴下面的代码插入 ProjectItemExtension 代码文件。  
  
    > [!NOTE]  
    >  添加此代码后，项目将出现一些编译错误。 在后续步骤中添加代码，这些错误将会消失。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>创建外部数据列表  
 添加的部分定义`GenerateExternalDataListsExtension`在 BDC 模型中创建的外部数据列表的每个实体的类。 若要创建外部数据列表，此代码将首先通过分析 BDC 模型文件中的 XML 数据读取 BDC 模型中的实体数据。 然后，它创建基于 BDC 模型并将此列表实例添加到项目的列表实例。  
  
#### <a name="to-create-the-external-data-lists"></a>若要创建外部数据列表  
  
1.  将以下代码粘贴到 GenerateExternalDataLists 代码文件。  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>检查点  
 此时在本演练中，项目项扩展的所有代码现在都是项目中。 生成解决方案以确保项目在编译时未出现错误。  
  
#### <a name="to-build-the-solution"></a>生成解决方案  
  
1.  在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>创建 VSIX 包来部署项目项扩展  
 若要部署的扩展，使用 VSIX 项目解决方案中创建 VSIX 包。 首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件中配置 VSIX 包。 然后，通过生成解决方案中创建 VSIX 包。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要配置并创建 VSIX 包  
  
1.  在**解决方案资源管理器**，在 GenerateExternalDataLists 项目中，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**打开**。  
  
     Visual Studio 将在清单编辑器中打开该文件。 Source.extension.vsixmanifest 文件是 extension.vsixmanifest 文件的基础所需的所有 VSIX 包。 有关此文件的详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**产品名称**框中，输入**外部数据列表生成器**。  
  
3.  在**作者**框中，输入**Contoso**。  
  
4.  在**说明**框中，输入**可以用于生成外部数据列表的业务数据连接模型项目项的扩展**。  
  
5.  上**资产**选项卡的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即出现。  
  
6.  在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于`MefComponent`extension.vsixmanifest 文件中的元素。 此元素指定的 VSIX 包中的扩展程序集的名称。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**源**列表中，选择**当前解决方案中的项目**。  
  
8.  在**项目**列表中，选择**BdcProjectItemExtension**，然后选择**确定**按钮。  
  
9. 在菜单栏上，依次选择 **“生成”**、 **“生成解决方案”**。  
  
10. 请确保该项目将编译并生成且未发生错误。  
  
11. 请确保 GenerateExternalDataLists 项目的生成输出文件夹现在包含 GenerateExternalDataLists.vsix 文件。  
  
     默认情况下，生成输出文件夹是...在包含你的项目文件的文件夹下的 \bin\Debug 文件夹。  
  
## <a name="testing-the-project-item-extension"></a>测试项目项扩展  
 现在你就可以测试项目项扩展。 首先，开始调试 Visual Studio 的实验实例中的扩展项目。 然后，使用 Visual Studio 的实验实例中扩展插件生成 BDC 模型的外部列表。 最后，打开要验证它按预期工作的 SharePoint 站点上的外部列表。  
  
#### <a name="to-start-debugging-the-extension"></a>若要开始调试扩展  
  
1.  如有必要，使用管理凭据，重新启动 Visual Studio，然后打开 GenerateExternalDataLists 解决方案。  
  
2.  在 BdcProjectItemExtension 项目中，打开 ProjectItemExtension 代码文件中，并将断点添加到中的代码行`Initialize`方法。  
  
3.  打开 GenerateExternalDataLists 代码文件中，并将断点添加到代码中的第一行`GenerateExternalDataLists_Execute`方法。  
  
4.  开始调试通过选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
     Visual Studio 将在 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External 数据列表 Generator\1.0 安装扩展，并启动 Visual Studio 的实验实例。 在 Visual Studio 的此实例中，将测试项目项。  
  
#### <a name="to-test-the-extension"></a>若要测试此扩展  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  在**新项目**对话框框中，展开**模板**节点，展开**Visual C#**节点，展开**SharePoint**节点，然后选择**2010年**。  
  
3.  在对话框顶部列表中，请确保**.NET Framework 3.5**选择。 为项目[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要此版本的.NET Framework。  
  
4.  在项目模板列表中，选择**SharePoint 2010 项目**。  
  
5.  在**名称**框中，输入**SharePointProjectTestBDC**，然后选择**确定**按钮。  
  
6.  在 SharePoint 自定义向导中，输入你想要使用的调试，请选择站点的 URL**部署为场解决方案**，然后选择**完成**按钮。  
  
7.  打开 SharePointProjectTestBDC 项目的快捷菜单，选择**添加**，然后选择**新项**。  
  
8.  在**添加 NewItem-SharePointProjectTestBDC**对话框框中，展开已安装的语言节点，展开**SharePoint**节点。  
  
9. 选择**2010年**节点，然后选择**业务数据连接模型 （仅场解决方案）**模板。  
  
10. 在**名称**框中，输入**TestBDCModel**，然后选择**添加**按钮。  
  
11. 验证在 Visual Studio 的其他实例中在代码停止在中设置的断点处`Initialize`ProjectItemExtension 代码文件的方法。  
  
12. 在 Visual Studio 的停止实例中，选择**F5**键，或在菜单栏上依次选择**调试**，**继续**以继续调试项目。  
  
13. 在 Visual Studio 的实验实例中，选择**F5**密钥，或在菜单栏上，选择**调试**，**启动调试**生成、 部署和运行**TestBDCModel**项目。  
  
     Web 浏览器将打开到为调试指定的 SharePoint 站点的默认页面。  
  
14. 验证**列出**部分的快速启动区域中尚不包含基于项目中的默认 BDC 模型的列表。 你必须先创建的外部数据列表中，通过使用 SharePoint 用户界面或通过使用项目项扩展。  
  
15. 关闭 web 浏览器。  
  
16. 在已经 TestBDCModel 项目打开的 Visual Studio 实例中，打开快捷菜单**TestBDCModel**中的节点**解决方案资源管理器**，然后选择**生成外部数据列表**。  
  
17. 验证在 Visual Studio 的其他实例中在代码停止在中设置的断点处`GenerateExternalDataLists_Execute`方法。 选择**F5**密钥，或在菜单栏上，选择**调试**，**继续**以继续调试项目。  
  
18. Visual Studio 的实验实例将添加名为的列表实例**Entity1DataList** TestBDCModel 到项目中和实例还会生成名为一种**功能 2**的列表实例。  
  
19. 选择**F5**密钥，或在菜单栏上，选择**调试**，**启动调试**生成、 部署和运行 TestBDCModel 项目。  
  
     Web 浏览器将打开到用于调试的 SharePoint 站点的默认页面。  
  
20. 在**列出**部分的快速启动区域中，选择**Entity1DataList**列表。  
  
21. 验证该列表包含名为 Identifier1 和消息，除了具有 0 Identifier1 值和 Hello World 消息值的一个项的列。  
  
     **业务数据连接模型**项目模板生成默认 BDC 模型，它提供所有这些数据。  
  
22. 关闭 web 浏览器。  
  
## <a name="cleaning-up-the-development-computer"></a>清理开发计算机  
 测试项目项扩展后，从 SharePoint 站点中删除外部列表和 BDC 模型，并从 Visual Studio 中删除项目项扩展。  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>若要从 SharePoint 站点中删除外部数据列表  
  
1.  在 SharePoint 站点的快速启动区域中，选择**Entity1DataList**列表。  
  
2.  在功能区中的 SharePoint 站点上，选择**列表**选项卡。  
  
3.  上**列表**选项卡上，在**设置**组中，选择**列表设置**。  
  
4.  下**权限和管理**，选择**删除此列表**，然后选择**确定**以确认你想要将此列表发送到回收站。  
  
5.  关闭 web 浏览器。  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>若要从 SharePoint 站点中删除 BDC 模型  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**生成**，**收回**。  
  
     Visual Studio 从 SharePoint 站点中删除 BDC 模型。  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>若要从 Visual Studio 中删除项目项扩展  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**外部数据列表生成器**，然后选择**卸载**按钮。  
  
3.  在显示的对话框中，选择**是**以确认你想要卸载扩展。  
  
4.  选择**立即重新启动**要完成卸载。  
  
5.  关闭 Visual Studio （实验实例和 GenerateExternalDataLists 解决方案处于打开状态的实例） 的两个实例。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  