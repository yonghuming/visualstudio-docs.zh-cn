---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects | Microsoft Docs"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  当您部署 SharePoint 项目时，Visual Studio 执行一系列部署步骤按特定顺序。  Visual Studio 包含许多内置部署步骤，但您也可以创建自己的部署步骤。  
  
 在本演练中，您将创建一个自定义部署步骤以升级运行 SharePoint 服务器的解决方案。  Visual Studio 包含针对许多任务，如收回或添加解决方案的内置部署步骤，但是，它不包含用于升级解决方案的部署步骤。  默认情况下，那么，当您部署 SharePoint 解决方案时，Visual Studio 会先收回该解决方案 \(如果已部署\) 然后重新部署整个解决方案。  有关内置部署步骤的更多信息，请参见[部署、发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
 本演练将演示以下任务：  
  
-   创建一个执行以下两大任务的 Visual Studio 扩展：  
  
    -   扩展定义自定义部署步骤以升级 SharePoint 解决方案。  
  
    -   扩展创建一个定义新的部署配置，即一组部署步骤为给定的项目执行的项目扩展。  新的部署配置包含自定义部署步骤和若干内置部署步骤。  
  
-   创建扩展程序集调用的两个自定义 SharePoint 命令。  SharePoint 命令是在服务器对象模型可由扩展程序集调用使用 API 为 SharePoint 的方法。  有关更多信息，请参见[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   生成 Visual Studio 扩展 \(VSIX\) 包以部署这两个程序集。  
  
-   测试新的部署步骤。  
  
## 系统必备  
 您需要在开发计算机上安装以下组件才能完成本演练：  
  
-   Windows、SharePoint 和 Visual Studio 的支持的版本。  有关更多信息，请参见[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。  本演练使用此 SDK 中的**“VSIX 项目”**模板来创建 VSIX 包以部署扩展。  有关更多信息，请参见[Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 了解以下概念很有用，但对于完成本演练并不是必需的：  
  
-   使用的 SharePoint 服务器对象模型。  有关更多信息，请参见 [Using the SharePoint Foundation Server\-Side Object Model](http://go.microsoft.com/fwlink/?LinkId=177796)（使用 SharePoint Foundation Server 端对象模型）。  
  
-   SharePoint 解决方案。  有关更多信息，请参见 [Solutions Overview](http://go.microsoft.com/fwlink/?LinkId=169422)（解决方案概述）。  
  
-   升级 SharePoint 解决方案。  有关更多信息，请参见 [Upgrading a Solution](http://go.microsoft.com/fwlink/?LinkId=177802)（升级解决方案）。  
  
## 创建项目  
 若要完成本演练，您必须创建三项：  
  
-   一个用于创建 VSIX 包以部署扩展的 VSIX 项目。  
  
-   一个用于实现扩展的类库项目。  此项目必须面向 .NET Framework 4.5。  
  
-   一个用于定义自定义 SharePoint 命令的类库项目。  此项目必须面向 .NET Framework 3.5。  
  
 从创建项目开始本演练。  
  
#### 创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
3.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **扩展性** 节点。  
  
    > [!NOTE]  
    >  只有在安装 Visual Studio SDK，**扩展性** 节点可用。  有关更多信息，请参见本主题前面的系统必备部分。  
  
4.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
5.  选择 **VSIX 项目** 模板，将项目命名为 **UpgradeDeploymentStep**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将**“UpgradeDeploymentStep”**项目添加到**“解决方案资源管理器”**中。  
  
#### 创建扩展项目  
  
1.  在 **解决方案资源管理器**，请打开 UpgradeDeploymentStep 解决方案节点的快捷菜单，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic** 节点，然后选择 **Windows** 节点。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 4.5**。  
  
4.  选择 **类库** 项目模板，将项目命名为 **DeploymentStepExtension**，然后选择 **确定** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将**“DeploymentStepExtension”**项目添加到解决方案中，并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
#### 创建 SharePoint 命令项目  
  
1.  在 **解决方案资源管理器**，请打开 UpgradeDeploymentStep 解决方案节点的快捷菜单，选择 **添加**，然后选择 **新建项目**。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，仅当在[“选项”对话框 \-\>“项目和解决方案”\-\>“常规”](http://msdn.microsoft.com/zh-cn/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca)中选中**“总是显示解决方案”**复选框时，解决方案节点才会出现在**“解决方案资源管理器”**中。  
  
2.  在 **新建项目** 对话框中，展开 **visual C\#** 或 **Visual Basic**，然后选择 **Windows** 节点。  
  
3.  在对话框顶部，选择在 .NET Framework 的版本列表的 **.NET Framework 3.5**。  
  
4.  选择 **类库** 项目模板，将项目命名为 **SharePointCommands**，然后选择 **确定** 按钮。  
  
     Visual Studio 会将**“SharePointCommands”**项目添加到解决方案中并打开默认的 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## 配置项目  
 在创建自定义部署步骤中编写代码，您必须先添加代码文件和程序集引用，因此，您必须配置项目。  
  
#### 配置 DeploymentStepExtension 项目  
  
1.  在 **DeploymentStepExtension** 项目中，添加两个具有下列名称的代码文件：  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  打开在 DeploymentStepExtension 项目的快捷菜单，然后选择 **添加引用**。  
  
3.  在 **框架** 选项，为 System.ComponentModel.Composition 程序集请选中复选框。  
  
4.  在 **扩展** 选项，为 Microsoft.VisualStudio.SharePoint 程序集请选中复选框，然后选择 **确定** 按钮。  
  
#### 配置 SharePointCommands 项目  
  
1.  在 **SharePointCommands** 项目中，添加名为 Commands 的代码文件。  
  
2.  在 **解决方案资源管理器**，打开在 **SharePointCommands** 项目节点的快捷菜单，然后选择 **添加引用**。  
  
3.  在 **扩展** 选项，以下程序集请选中复选框，然后单击选项 **确定** 按钮  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## 定义自定义部署步骤  
 创建一个定义升级部署步骤的类。  若要定义部署步骤，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 接口。  每当需要定义自定义部署步骤时，就要实现此接口。  
  
#### 定义自定义部署步骤  
  
1.  在 **DeploymentStepExtension** 项目中，打开 UpgradeStep 代码文件，然后将下面的代码粘贴到它。  
  
    > [!NOTE]  
    >  在添加此代码后，项目将会出现一些编译错误，但是，它们将消失，当您将在后面的步骤中代码。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## 创建包含自定义部署步骤的部署配置  
 创建新的部署配置的项目扩展，包括若干内置部署步骤和新的升级部署步骤。  通过创建此扩展，可以在 SharePoint 项目帮助 SharePoint 开发人员使用升级部署步骤。  
  
 若要创建部署配置，此类应实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 接口。  每当需要创建 SharePoint 项目扩展时，就要实现此接口。  
  
#### 创建部署配置  
  
1.  在 **DeploymentStepExtension** 项目中，打开 DeploymentConfigurationExtension 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## 创建自定义 SharePoint 命令  
 创建的调入 SharePoint 服务器对象模型的两个自定义命令。  一个命令用于确定是否已部署解决方案；另一个命令用于升级解决方案。  
  
#### 定义 SharePoint 命令  
  
1.  在 **SharePointCommands** 项目中，打开 commands 代码文件，然后将下面的代码粘贴到它。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## 检查点  
 演练进行到此时，自定义部署步骤和 SharePoint 命令的所有代码都位于项目中。  编译它们，以确保它们编译时不会出错。  
  
#### 生成项目  
  
1.  在 **解决方案资源管理器**，打开 **DeploymentStepExtension** 项目的快捷菜单，然后选择 **Build**。  
  
2.  打开 **SharePointCommands** 项目的快捷菜单，然后选择 **Build**。  
  
## 创建 VSIX 包以部署扩展  
 若要部署扩展，请使用解决方案中的 VSIX 项目来创建 VSIX 包。  首先，通过修改 VSIX 项目中的 source.extension.vsixmanifest 文件来配置 VSIX 包。  然后通过生成解决方案创建 VSIX 包。  
  
#### 配置并创建 VSIX 包  
  
1.  在 **解决方案资源管理器**，在 **UpgradeDeploymentStep** 项目中，打开 **source.extension.vsixmanifest** 文件的快捷菜单，然后选择 **打开**。  
  
     Visual Studio 将在清单编辑器中打开该文件。  source.extension.vsixmanifest 文件是所有 VSIX 包必需的 extension.vsixmanifest 文件的基础。  有关此文件的更多信息，请参见[VSIX 扩展架构参考](http://msdn.microsoft.com/zh-cn/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在 **产品名称** 框中，输入 **升级 SharePoint 项目的部署步骤**。  
  
3.  在 **作者** 框中，输入 **Contoso**。  
  
4.  在 **说明** 框中，输入 **提供可用于 SharePoint 项目的自定义升级部署步骤**。  
  
5.  在编辑器中 **资产** 选项卡中，选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
6.  在 **类型** 列表中，选择 **Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于 extension.vsixmanifest 文件中的 `MefComponent` 元素。  此元素指定 VSIX 包中的扩展程序集的名称。  有关更多信息，请参见[NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/zh-cn/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
8.  在 **项目** 列表中，选择 **DeploymentStepExtension**，然后选择 **确定** 按钮。  
  
9. 在清单编辑器，请选择 **新建** 按钮。  
  
     **添加新资产** 出现对话框。  
  
10. 在 **类型** 列表中，输入 **SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  此元素指定要包括在 Visual Studio 扩展中的自定义扩展。  有关更多信息，请参见[属性元素 \(VSX 架构\)](http://msdn.microsoft.com/zh-cn/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在 **源** 列表中，选择 **当前解决方案中的项目**。  
  
12. 在 **项目** 列表中，选择 **SharePointCommands**，然后选择 **确定** 按钮。  
  
13. 在菜单栏上，依次选择 **Build**，**生成解决方案**，然后确保解决方案已生成且未发生错误。  
  
14. 确保 UpgradeDeploymentStep 项目的生成输出文件夹现在包含 UpgradeDeploymentStep.vsix 文件。  
  
     默认情况下，生成输出文件夹为  包含项目文件的文件夹下的 ..\\bin\\Debug 文件夹。  
  
## 准备测试升级部署步骤  
 若要测试升级部署步骤，您必须先将示例解决方案部署到 SharePoint 网站中。  首先在 Visual Studio 的实验实例中调试扩展。  然后创建一个列表定义和列表实例用于测试部署步骤，然后将它们部署到 SharePoint 网站。  接下来，将修改列表定义和列表实例并对其进行重新部署演示默认部署过程如何复盖 SharePoint 网站的解决方案。  
  
 在本演练中，您将修改列表定义和列表实例，必须在 SharePoint 站点然后将它们升级。  
  
#### 开始调试扩展  
  
1.  重新启动使用管理凭据的 Visual Studio，然后打开 UpgradeDeploymentStep 解决方案。  
  
2.  在 DeploymentStepExtension 项目中，打开 UpgradeStep 代码文件，然后将断点添加到第一个代码行中 `CanExecute` 和 `Execute` 方法的。  
  
3.  开始调试通过选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
4.  Visual Studio 将扩展安装到 %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ upgrade deployment step SharePoint 项目的\\ 1.0 中启动 Visual Studio 的实验实例。  在此实例中测试升级部署步骤 Visual Studio。  
  
#### 若要创建 SharePoint 项目与列表定义和列表实例  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **文件**，**新建**，**项目**。  
  
2.  在 **新建项目** 对话框中，展开 **visual C\#** 节点或 **Visual Basic** 节点，展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
3.  在对话框顶部，确保 **.NET Framework 3.5** 出现在 .NET Framework 的版本列表。  
  
     针对 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 的项目需要此版本的 .NET Framework。  
  
4.  在项目模板列表中，选择 **SharePoint 2010 项目**，将项目命名为 **EmployeesListDefinition**，然后选择 **确定** 按钮。  
  
5.  在 **SharePoint 自定义向导**，输入要用于调试的网站的 URL。  
  
6.  在 **此 SharePoint 解决方案的信任级别是什么**下，选择 **部署为场解决方案** 选项按钮。  
  
    > [!NOTE]  
    >  升级部署步骤不支持沙盒解决方案。  
  
7.  选择 **完成** 按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建 EmployeesListDefinition 项目。  
  
8.  打开 EmployeesListDefinition 项目的快捷菜单，选择 **添加**，然后选择 **新建项**。  
  
9. 在 **添加新项目– EmployeesListDefinition** 对话框中，展开 **SharePoint** 节点，然后选择 **2010** 节点。  
  
10. 选择 **列表** 项目模板，将项目命名为 **雇员列表**，然后选择 **添加** 按钮。  
  
     SharePoint 自定义向导显示  
  
11. 在 **选择列表设置** 页中，验证以下设置，然后选择 **完成** 按钮：  
  
    1.  **雇员列表** 出现在 **您希望列表的显示名称是什么？** 框。  
  
    2.  **创建自定义基于列表：** 选项按钮中选择。  
  
    3.  **默认 \(空白\)** 在 **创建自定义基于列表：** 列表中选择项。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建雇员列表与标题列和一个空实例中的项目并打开列表设计器。  
  
12. 在列表中，设计器 **栏** 选项卡上，选择 **键入新的或现有的列名称** 行，然后添加到 **列显示名称** 的下列列表：  
  
    1.  名字  
  
    2.  公司  
  
    3.  业务电话  
  
    4.  电子邮件  
  
13. 保存所有文件，然后关闭列表设计器。  
  
14. 在 **解决方案资源管理器**，展开 **雇员列表** 节点，然后展开 **雇员列表实例** 子节点。  
  
15. 在 Elements.xml 文件中，用以下 XML 替换该文件的默认 XML。  此 XML 可以将列表的名称。**员工** 并添加名为 jim Hance 名称雇员的信息。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. 保存并关闭 Elements.xml 文件。  
  
17. 打开 EmployeesListDefinition 项目的快捷菜单，然后选择 **打开** 或 **属性**。  
  
     属性设计器中打开。  
  
18. 在 **SharePoint** 选项卡上，清除 **调试后自动收回** 复选框，然后保存属性。  
  
#### 部署列表定义和列表实例  
  
1.  在 **解决方案资源管理器**，选择 **EmployeesListDefinition** 项目节点。  
  
2.  在**“属性”**窗口中，确保将**“活动部署配置”**属性设置为**“默认”**。  
  
3.  选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
4.  验证项目成功生成，则浏览器将打开 SharePoint 站点，在快速启动栏中的 **列表** 项目包括新的 **员工** 列表和 **员工** 列表包括 jim Hance 对应的项。  
  
5.  关闭该浏览器。  
  
#### 修改列表定义和列表实例并对其进行重新部署  
  
1.  在 EmployeesListDefinition 项目中，打开是 **雇员列表实例** 项目项的子级的 Elements.xml 文件。  
  
2.  移除 `Data` 元素及其子级，以便从列表中移除与 Jim Hance 对应的项。  
  
     完成后，文件应包含以下 XML。  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  保存并关闭 Elements.xml 文件。  
  
4.  打开 **雇员列表** 项目项的快捷菜单，然后选择 **打开** 或 **属性**。  
  
5.  在列表中设计器中，选择 **视图** 选项。  
  
6.  在 **选定的列** 列表中，选择 **附件**，然后选择 \< 键将该列移动到 **可用列** 列表。  
  
7.  重复上述步骤从 **选定的列** 移动 **业务电话** 列列表。**可用列** 列表。  
  
     此操作将从 SharePoint 网站上的**“Employees”（雇员）**列表的默认视图中移除这些字段。  
  
8.  开始调试通过选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
9. 验证**“部署冲突”**对话框是否出现。  
  
     此对话框显示 Visual Studio 尝试部署解决方案 \(列表实例\) 添加到该解决方案已部署的 SharePoint 站点。  此对话框不会显示在以后执行升级部署步骤在本演练中。  
  
10. 在 **部署冲突** 对话框中，选择 **自动解决** 选项按钮。  
  
     Visual Studio 将删除 SharePoint 网站上的列表实例，在项目中部署项列表，然后打开 SharePoint 站点。  
  
11. 在快速启动栏中的 **列表** 部分中，选择 **员工** 列表，然后验证以下详细信息：  
  
    -   **附件** 和 **家庭电话** 列未显示在此列表视图中。  
  
    -   该列表为空。  之前使用**“默认”**部署配置重新部署解决方案时，**“Employees”（雇员）**列表已替换为项目中的新的空列表。  
  
## 测试部署步骤  
 现在您可以对升级部署步骤进行测试了。  首先，向 SharePoint 中的列表实例添加一个项。  然后更改列表定义和列表实例，将它们升级到 SharePoint 网站，并确认升级部署步骤不会复盖新项。  
  
#### 手动向列表添加项  
  
1.  在 SharePoint 网站上的功能区，在 **列表工具** 选项卡下，选择 **项** 选项。  
  
2.  在 **新建** 组中，选择 **新建项**。  
  
     或者，可以选择在项目的 **添加新项目** 链接列表。  
  
3.  在 **雇员–新项目** 窗口，请在 **标题** 框中，输入 **结构管理器**。  
  
4.  在 **名字** 框中，输入 **安迪**。  
  
5.  在 **公司** 框中，键入 **Contoso**。  
  
6.  选择 **保存** 按钮，验证新项出现在列表中，然后关闭该浏览器。  
  
     在本演练中，您将使用此项验证升级部署步骤不会复盖此列表的内容。  
  
#### 测试升级部署步骤  
  
1.  在 Visual Studio 的实验实例中，在 **解决方案资源管理器**，打开 **EmployeesListDefinition** 项目节点的快捷菜单，然后选择 **属性**。  
  
     属性编辑器或设计器中打开。  
  
2.  在 **SharePoint** 选项卡上，将 **活动部署配置** 属性设置为 **升级**。  
  
     此自定义部署配置包含新的升级部署步骤。  
  
3.  打开 **雇员列表** 项目项的快捷菜单，然后选择 **属性** 或 **打开**。  
  
     属性编辑器或设计器中打开。  
  
4.  在 **视图** 选项卡中，选择 **电子邮件** 列，然后选择 **\<** 键移动从 **选定的列** 的列列表。**可用列** 列表。  
  
     此操作将从 SharePoint 网站上的**“Employees”（雇员）**列表的默认视图中移除这些字段。  
  
5.  开始调试通过选择 F5 键或，在菜单栏上，选择 **调试**，**启动调试**。  
  
6.  验证另一个 Visual Studio 实例中的代码是否会在您之前在 `CanExecute` 方法中设置的断点处停止。  
  
7.  再次选择 F5 键或，在菜单栏上，选择 **调试**，**继续**。  
  
8.  验证代码是否会在您之前在 `Execute` 方法中设置的断点处停止。  
  
9. 选择 F5 键或，在菜单栏上，选择 **调试**，**继续** 最后一时间。  
  
     在 web 浏览器中打开 SharePoint 站点。  
  
10. 在快速启动区域的 **列表** 部分中，选择 **员工** 列表，然后验证以下详细信息：  
  
    -   先前手动添加的项 \(对于安迪，结构管理器\) 仍在列表中。  
  
    -   **业务电话** 和 **电子邮件地址** 列未显示在此列表视图中。  
  
     **“升级”**部署配置将修改 SharePoint 网站上的现有**“Employees”（雇员）**列表实例。  如果使用的是**“默认”**部署配置，而不是**“升级”**配置，则会遇到部署冲突。  Visual Studio 将通过替换 **员工** 解决冲突列表，并且，安迪的项目，结构管理器中，将被删除。  
  
## 清理开发计算机  
 测试完升级部署步骤之后，请从 SharePoint 网站中移除列表实例和列表定义，并从 Visual Studio 中移除部署步骤扩展。  
  
#### 从 SharePoint 网站中移除列表实例  
  
1.  如果列表尚未打开，打开 **员工** 列出了 SharePoint 站点。  
  
2.  在 SharePoint 网站上的功能区，选择 **列表工具** 选项卡，然后选择 **列表** 选项。  
  
3.  在 **设置** 组中，选择 **列表设置** 项目。  
  
4.  在 **权限和管理**下，选择 **删除此列表** 命令，选择 **确定** 确认要将此列表发送到"回收站"，然后关闭该浏览器。  
  
#### 从 SharePoint 网站中移除列表定义  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **Build**，**收回**。  
  
     Visual Studio 将从 SharePoint 网站收回列表定义。  
  
#### 卸载扩展  
  
1.  在 Visual Studio 的实验实例中，在菜单栏上，依次选择 **工具**，**扩展和更新**。  
  
     **扩展和更新** 对话框打开。  
  
2.  在扩展列表中，选择 **升级 SharePoint 项目的部署步骤**，然后选择 **卸载** 命令。  
  
3.  在出现的对话框中，选择 **是** 确认要卸载该扩展，然后选择 **立即重新启动** 完成卸载。  
  
4.  关闭 Visual Studio 的实验实例 \(和 UpgradeDeploymentStep 解决方案处于打开状态的实例\) 两个实例 Visual Studio。  
  
## 请参阅  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  