---
title: "Walkthrough: Extending a SharePoint Project Item Type"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  可以使用**“业务数据连接模型”**项目项来为 SharePoint 中的业务数据连接 \(BDC\) 服务创建模型。  默认情况下，当使用此项目项创建模型时，不会向用户显示模型中的数据。  您还必须在 SharePoint 中创建一个外部列表，这样用户才能查看数据。  
  
 在本演练中，您将为**“业务数据连接模型”**项目项创建一个扩展。  开发人员可以使用此扩展在其项目中创建一个外部列表，以用来显示 BDC 模型中的数据。  本演练将演示以下任务：  
  
-   创建一个执行以下两大任务的 Visual Studio 扩展：  
  
    -   此扩展生成一个用于显示 BDC 模型中的数据的外部列表。  此扩展使用 SharePoint 项目系统的对象模型来生成一个用于定义列表的 Elements.xml 文件。  此扩展还将该文件添加到项目中，以便将该文件与 BDC 模型一起部署。  
  
    -   此扩展将一个快捷菜单项添加到**“解决方案资源管理器”**的**“业务数据连接模型”**项目项中。  开发人员可以单击此菜单项来为 BDC 模型生成一个外部列表。  
  
-   生成 Visual Studio 扩展 \(VSIX\) 包来部署扩展程序集。  
  
-   测试扩展。  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   支持的 Microsoft Windows、SharePoint 和 Visual Studio 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。  本演练使用 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署项目项。  有关详细信息，请参阅[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 中的 BDC 服务。  有关详细信息，请参阅 [BDC 体系结构](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   BDC 模型的 XML 架构。  有关详细信息，请参阅 [BDC 模型 基础架构](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## 创建项目  
 若要完成本演练，您需要创建以下两个项目：  
  
-   一个用于创建 VSIX 包以部署项目项扩展的 VSIX 项目。  
  
-   一个用于实现项目项扩展的类库项目。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在**“新建项目”**对话框中，展开**“Visual C\#”**或**“Visual Basic”**节点，然后选择**“扩展性”**节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio 2010 SDK 之后，**“扩展性”**节点才可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
4.  在**“新建项目”**对话框的顶部列表中，选择**“.NET Framework 4.5”**。  
  
     SharePoint 工具扩展需要此版本的 .NET Framework 中的功能。  
  
5.  选择 **VSIX 项目** 模板  
  
6.  在**“名称”**文本框中，输入 **GenerateExternalDataLists**,然后选择 **“确定”** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将**“GenerateExternalDataLists”**项目添加到**“解决方案资源管理器”**中。  
  
7.  如果 source.extension.vsixmanifest 文件没有自动打开，请打开其在 GenerateExternalDataLists 项目的快捷菜单，然后选择 **打开**  
  
8.  验证 source.extension.vsixmanifest 文件具有非空白项 \(输入 Contoso\) 在作者字段，将该文件保存并关闭。  
  
#### 创建扩展项目  
  
1.  在**“解决方案资源管理器”**中，打开 **GenerateExternalDataLists** 解决方案节点的快捷菜单，选择 **添加**, 然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在**“添加新项目”**对话框中，展开**“Visual C\#”**或**“Visual Basic”**节点，然后单击**“窗口”**节点。  
  
3.  在对话框顶部的列表中，选择**“.NET Framework 4.5”**。  
  
4.  在项目模板列表中，选择**“类库”**。  
  
5.  在**“名称”**文本框中，输入 **BdcProjectItemExtension**, 然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“BdcProjectItemExtension”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
6.  从项目中删除 Class1 代码文件。  
  
## 配置扩展项目  
 在编写代码以创建项目项扩展之前，请将代码文件和程序集引用添加到扩展项目中。  
  
#### 配置项目  
  
1.  在 BdcProjectItemExtension 项目中添加两个具有下列名称的代码文件：  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  选择 BdcProjectItemExtension 项目，然后在菜单栏上，选择 **项目**，**添加引用**。  
  
3.  在 **程序集** 节点下，选择 **框架** 节点并选择以下程序集中的复选框：  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  在 **程序集** 节点下，选择 **扩展** 节点，然后为以下程序集选择复选框：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  选择**“确定”**按钮。  
  
## 定义项目项扩展  
 创建一个定义**“业务数据连接模型”**项目项扩展的类。  若要定义扩展，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 接口。  每当需要扩展现有类型的项目项时，就要实现此接口。  
  
#### 定义项目项扩展  
  
1.  将下面的代码粘贴到 ProjectItemExtension 代码文件。  
  
    > [!NOTE]  
    >  添加此代码后，项目将会出现一些编译错误。  在添加后面的步骤中的代码之后，这些错误将消失。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## 创建外部数据列表  
 添加 `GenerateExternalDataListsExtension` 类的分部定义，该类为 BDC 模型中的每个实体创建一个外部数据列表。  若要创建外部数据列表，此代码应首先通过分析 BDC 模型文件中的 XML 数据，读取 BDC 模型中的实体数据。  然后，此代码基于 BDC 模型创建一个列表实例，并将此列表实例添加到项目中。  
  
#### 创建外部数据列表  
  
1.  复制下面的代码并将其粘贴到 GenerateExternalDataLists 代码文件中。  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## 检查点  
 演练进行到此时，项目项扩展的所有代码都位于项目中。  生成解决方案以确保编译项目时不会出错。  
  
#### 生成解决方案  
  
1.  在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
## 创建 VSIX 包以部署项目项扩展  
 若要部署扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中包含的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后，通过生成解决方案来创建 VSIX 包。  
  
#### 配置并创建 VSIX 包  
  
1.  在**“解决方案资源管理器”**中打开 GenerateExternalDataLists 项目中 source.extension.vsixmanifest 文件的快捷菜单，然后依次选择**“打开”**。  
  
     Visual Studio 将在清单编辑器中打开该文件。  source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**“产品名称”**框中键入**“外部数据列表生成器”**。  
  
3.  在**“作者”**框中键入 **Contoso**。  
  
4.  在**“说明”**框中，键入**“可用于生成外部数据列表的业务数据连接模型项目项的扩展”**。  
  
5.  在编辑器的 **资产** 选项卡中，选择 **新建** 按钮。  
  
     **“添加新项”**对话框随即出现。  
  
6.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.ItemTemplate**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关详细信息，请参阅[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
8.  在**“项目”**列表中，选择**BdcProjectItemExtension**，然后选择**“确定”**按钮。  
  
9. 在菜单栏上，依次选择**“生成”**、**“生成解决方案”**。  
  
10. 确保编译和生成项目时不会出错。  
  
11. 确保 GenerateExternalDataLists 项目的生成输出文件夹现在包含 GenerateExternalDataLists.vsix 文件。  
  
     默认情况下，生成输出文件夹为 ..\\bin\\debug 文件夹, 位于包含您的项目文件的文件夹下。  
  
## 测试项目项扩展  
 现在您可以对项目项扩展进行测试了。  首先，在 Visual Studio 的实验实例中开始调试扩展项目。  然后，在 Visual Studio 的实验实例中使用扩展以生成 BDC 模型的外部列表。  最后，打开 SharePoint 网站上的外部列表，以验证该列表是否按预期方式工作。  
  
#### 开始调试扩展  
  
1.  如果需要，使用管理员凭证重新启动 Visual Studio，然后打开 GenerateExternalDataLists 解决方案。  
  
2.  在 BdcProjectItemExtension 项目中，打开 ProjectItemExtension 代码文件，然后在 `Initialize` 方法的代码行中添加一个断点。  
  
3.  打开 GenerateExternalDataLists 代码文件，然后在 `GenerateExternalDataLists_Execute` 方法的第一行代码中添加一个断点。  
  
4.  通过选择 F5 键或在菜单栏上，选择 **调试**，**启动调试**开始调试。  
  
     Visual Studio 将扩展安装到 %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\External Data List Generator\\1.0 中，并启动 Visual Studio 的实验实例。  您将在此 Visual Studio 实例中测试项目项。  
  
#### 测试扩展  
  
1.  在 Visual Studio 的实验实例中，在**“文件”**菜单上指向**“新建”**，然后单击**“项目”**。  
  
2.  在**“新建项目”**对话框中，依次展开**“模板”**节点、**Visual C\#**节点、**SharePoint** 节点，然后选择 **2010**.。  
  
3.  在对话框顶部的列表中，确保选中 **“.NET Framework 3.5”**。  [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 项目需要此版本的 .NET Framework。  
  
4.  在项目模板的列表中，单击**“SharePoint 2010 项目”**。  
  
5.  在**“名称”**文本框中，输入 **SharePointProjectTestBDC**，然后选择 **“确定”** 按钮。  
  
6.  在 SharePoint 自定义向导中，输入要调试的网站的 URL，选择 **部署为场解决方案**，然后选择 **完成**按钮。  
  
7.  打开 SharePointProjectTestBDC 的项目的快捷菜单，选择**“添加”**，然后选择 **“新项”**。  
  
8.  在 **添加 NewItem（新项） – SharePointProjectTestBDC** 对话框中，展开安装的语言节点，展开 **SharePoint** 节点。  
  
9. 选择 **2010** 节点，然后选择 **业务数据连接模型 \(仅场解决方案\)** 模板。  
  
10. 在**“名称”**框中输入 **TestBDCModel**, 然后选择 **“添加”** 按钮。  
  
11. 验证另一个 Visual Studio 实例中的代码会在您在 ProjectItemExtension 代码文件的 `Initialize` 方法中设置的断点处停止。  
  
12. 在 Visual Studio 停止的实例中，选则 **F5** 键，或者在菜单栏上，选择 **调试**，**继续** 继续调试项目。  
  
13. 在 Visual Studio 的实验实例中，选择 **F5** 键或者，在菜单栏上，选择 **调试**，**启动调试** 生成，部署，并且运行 **TestBDCModel** 项目。  
  
     Web 浏览器将打开用于调试的 SharePoint 网站的默认页面。  
  
14. 确认快速启动区域中的**“列表”**部分尚未包含基于项目中的默认 BDC 模型的列表。  您首先必须通过使用 SharePoint 用户界面或通过使用项目项扩展，创建一个外部数据列表。  
  
15. 关闭 Web 浏览器。  
  
16. 在Visual Studio 中已打开的 TestBDCModel 项目的实例中，打开**“解决方案资源管理器”**中的**“TestBDCModel”**节点的快捷菜单，再单击**“生成外部数据列表”**。  
  
17. 验证另一个 Visual Studio 实例中的代码会在您之前在 `GenerateExternalDataLists_Execute` 方法中设置的断点处停止。  选择 **F5** 键或者，在菜单栏上，选择 **调试**，**继续** 继续调试项目。  
  
18. Visual Studio 的实验实例将向 TestBDCModel 项目中添加名为**“Entity1DataList”**的列表实例，并且还将为该列表实例生成一项名为**“Feature2”**的功能。  
  
19. 选择 **F5** 键或者，在菜单栏上，选择 **调试**，**启动调试** 生成，部署，并且运行 TestBDCModel 项目。  
  
     Web 浏览器将打开用于调试的 SharePoint 网站的默认页面。  
  
20. 在快速启动区域的 **Lists** 部分，选择 **Entity1DataList** 列表。  
  
21. 确认该列表包含名为 Identifier1 和 Message 的列，并包含一个值为 “0” 的 Identifier1 且值为 “Hello World” 的 Message的项。  
  
     **业务数据链接模型** 项目模板生成默认 BDC 模型用于提供所有的数据.  
  
22. 关闭 Web 浏览器。  
  
## 清理开发计算机  
 完成测试项目项扩展之后，从 SharePoint 网站中移除外部列表和 BDC 模型，并从 Visual Studio 中移除项目项扩展。  
  
#### 从 SharePoint 网站中移除外部数据列表  
  
1.  在 SharePoint 网站的快速启动区域中，选择**“Entity1DataList”**列表。  
  
2.  在 SharePoint 网站上的功能区中，选择**“列表”**选项卡。  
  
3.  在**“列表”**选项卡上的**“设置”**组中，选择**“列表设置”**。  
  
4.  在 **权限和管理**下，选择 **删除此列表**，然后选择 **确定** 以确认要将此列表发送到回收站。  
  
5.  关闭 Web 浏览器。  
  
#### 从 SharePoint 网站中移除 BDC 模型  
  
1.  在 Visual Studio 的实验实例中，在菜单上依次选择**“生成”**，**“收回”**。  
  
     Visual Studio 将从 SharePoint 网站中移除 BDC 模型。  
  
#### 从 Visual Studio 中移除项目项扩展  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上选择 **“工具”**，**“扩展管理器”**。  
  
     “扩展和更新”对话框将打开。  
  
2.  在扩展列表中，选择**“外部数据列表生成器”**，然后单击**“卸载”**按钮。  
  
3.  在出现的对话框中，单击**“是”**以确认您要卸载该扩展。  
  
4.  单击**“立即重新启动”**以完成卸载。  
  
5.  关闭 Visual Studio 的两个实例（Visual Studio 的实验实例和已在 GenerateExternalDataLists 解决方案中打开的实例）。  
  
## 请参阅  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  