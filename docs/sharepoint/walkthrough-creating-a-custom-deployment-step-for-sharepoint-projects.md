---
title: "演练： 为 SharePoint 项目创建自定义部署步骤 |Microsoft 文档"
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
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b7375071522ea59c9c00a5fa94277a3817438d25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>演练：为 SharePoint 项目创建自定义部署步骤
  在部署 SharePoint 项目时，Visual Studio 以特定顺序执行一系列部署步骤。 Visual Studio 提供了许多内置部署步骤，但你也可以创建你自己。  
  
 在本演练中，将创建自定义部署步骤以升级运行 SharePoint 的服务器上的解决方案。 Visual Studio 提供了内置部署步骤对许多任务中，将此类收回或添加解决方案，但它不包含升级解决方案的部署步骤。 默认情况下，当你部署 SharePoint 解决方案，Visual Studio 首先将收回解决方案 （如果已部署） 和再将重新部署整个解决方案。 有关内置部署步骤的详细信息，请参阅[部署、 发布和升级 SharePoint 解决方案包](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)。  
  
 本演练演示了下列任务：  
  
-   创建一个 Visual Studio 扩展来执行两项主要任务：  
  
    -   扩展定义自定义部署步骤以升级 SharePoint 解决方案。  
  
    -   扩展来创建项目扩展，用于定义一个新的部署配置，这是一组针对给定项目执行的部署步骤。 新的部署配置包括自定义部署步骤和几个内置部署步骤。  
  
-   创建两个扩展程序集调用的自定义 SharePoint 命令。 SharePoint 命令是要用于 SharePoint Api 在服务器对象模型中的扩展程序集可以调用的方法。 有关详细信息，请参阅[调入 SharePoint 对象模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
-   生成 Visual Studio 扩展 (VSIX) 包以部署这两个程序集。  
  
-   测试新的部署步骤。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练的开发计算机上：  
  
-   受支持的 Windows、 SharePoint 和 Visual Studio 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio SDK。 本演练使用**VSIX 项目**创建 VSIX 包来部署该扩展 SDK 中的模板。 有关详细信息，请参阅[扩展 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 以下概念的知识将会很有用，但不是要求必须完成本演练：  
  
-   使用 SharePoint 服务器对象模型。 有关详细信息，请参阅[使用 SharePoint Foundation 服务器端对象模型](http://go.microsoft.com/fwlink/?LinkId=177796)。  
  
-   SharePoint 解决方案。 有关详细信息，请参阅[解决方案概述](http://go.microsoft.com/fwlink/?LinkId=169422)。  
  
-   升级 SharePoint 解决方案。 有关详细信息，请参阅[升级解决方案](http://go.microsoft.com/fwlink/?LinkId=177802)。  
  
## <a name="creating-the-projects"></a>创建项目  
 若要完成本演练，必须创建三个项目：  
  
-   若要创建 VSIX 包来部署扩展一个 VSIX 项目。  
  
-   用于实现扩展的类库项目。 此项目必须面向.NET Framework 4.5。  
  
-   定义自定义 SharePoint 命令的类库项目。 此项目必须面向.NET Framework 3.5。  
  
 首先演练创建项目。  
  
#### <a name="to-create-the-vsix-project"></a>若要创建 VSIX 项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
3.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**扩展性**节点。  
  
    > [!NOTE]  
    >  **扩展性**节点是安装 Visual Studio SDK 时才可用。 有关详细信息，请参阅本主题前面的先决条件部分。  
  
4.  在对话框中的顶部，选择**.NET Framework 4.5**在列表中的.NET framework 的版本。  
  
5.  选择**VSIX 项目**模板，将项目**UpgradeDeploymentStep**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**UpgradeDeploymentStep**项目合并为**解决方案资源管理器**。  
  
#### <a name="to-create-the-extension-project"></a>若要创建扩展项目  
  
1.  在**解决方案资源管理器**，打开 UpgradeDeploymentStep 解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**节点，然后选择**Windows**节点。  
  
3.  在对话框中的顶部，选择**.NET Framework 4.5**在列表中的.NET framework 的版本。  
  
4.  选择**类库**项目模板，将项目**DeploymentStepExtension**，然后选择**确定**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将添加**DeploymentStepExtension**到解决方案的项目并打开默认 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
#### <a name="to-create-the-sharepoint-command-project"></a>若要创建 SharePoint 命令项目  
  
1.  在**解决方案资源管理器**，打开 UpgradeDeploymentStep 解决方案节点的快捷菜单，选择**添加**，然后选择**新项目**。  
  
2.  在**新项目**对话框框中，展开**Visual C#**或**Visual Basic**，然后选择**Windows**节点。  
  
3.  在对话框中的顶部，选择**.NET Framework 3.5**在列表中的.NET framework 的版本。  
  
4.  选择**类库**项目模板，将项目**SharePointCommands**，然后选择**确定**按钮。  
  
     Visual Studio 将添加**SharePointCommands**到解决方案的项目并打开默认 Class1 代码文件。  
  
5.  从项目中删除 Class1 代码文件。  
  
## <a name="configuring-the-projects"></a>配置项目  
 在编写代码以创建自定义部署步骤之前，你必须将代码文件和程序集引用和你必须将项目配置。  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>若要配置 DeploymentStepExtension 项目  
  
1.  在**DeploymentStepExtension**项目中，添加具有以下名称的两个代码文件：  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  打开上 DeploymentStepExtension 项目的快捷菜单，然后选择**添加引用**。  
  
3.  上**Framework**选项卡上，为 System.ComponentModel.Composition 程序集中选择复选框。  
  
4.  上**扩展**选项卡上，对于 Microsoft.VisualStudio.SharePoint 程序集，选中的复选框，然后选择**确定**按钮。  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>若要配置 SharePointCommands 项目  
  
1.  在**SharePointCommands**项目中，添加名为命令的代码文件。  
  
2.  在**解决方案资源管理器**，打开快捷菜单上**SharePointCommands**项目节点，，然后选择**添加引用**。  
  
3.  上**扩展**选项卡上，为以下程序集，选择复选框，然后单击选择**确定**按钮  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>定义自定义部署步骤  
 创建定义升级部署步骤的类。 若要定义部署步骤，此类应实现<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>接口。 无论何时你想要定义自定义部署步骤，请实现此接口。  
  
#### <a name="to-define-the-custom-deployment-step"></a>若要定义自定义部署步骤  
  
1.  在**DeploymentStepExtension**项目中，打开 UpgradeStep 代码文件中，，然后将以下代码粘贴到其中。  
  
    > [!NOTE]  
    >  添加此代码，此项目将具有某些编译错误，但它们将消失之后时你将代码添加在后来的步骤。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>创建部署配置，包括自定义部署步骤  
 创建项目扩展为新的部署配置，其中包括几个内置部署步骤和新的升级部署步骤。 通过创建此扩展，可帮助 SharePoint 开发人员可以在 SharePoint 项目中使用了升级部署步骤。  
  
 若要创建的部署配置，此类应实现<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>接口。 无论何时你想要创建 SharePoint 项目扩展，则实现此接口。  
  
#### <a name="to-create-the-deployment-configuration"></a>若要创建的部署配置  
  
1.  
  
2.  在**DeploymentStepExtension**项目中，打开 DeploymentConfigurationExtension 代码文件中，，然后将以下代码粘贴到其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>创建自定义 SharePoint 命令  
 创建 SharePoint 连接到服务器对象模型的两个自定义命令。 一个命令将确定是否已部署解决方案时;其他命令升级解决方案。  
  
#### <a name="to-define-the-sharepoint-commands"></a>若要定义 SharePoint 命令  
  
1.  在**SharePointCommands**项目中，打开命令代码文件中，，然后将以下代码粘贴到其中。  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>检查点  
 此时在演练中，自定义部署步骤和 SharePoint 命令的所有代码都现将位于项目。 生成它们以确保它们在编译时未出现错误。  
  
#### <a name="to-build-the-projects"></a>若要生成项目  
  
1.  在**解决方案资源管理器**，打开快捷菜单**DeploymentStepExtension**项目，，然后选择**生成**。  
  
2.  打开的快捷菜单**SharePointCommands**项目，，然后选择**生成**。  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>创建 VSIX 包来部署扩展  
 若要部署的扩展，使用 VSIX 项目解决方案中创建 VSIX 包。 首先，通过修改 VSIX 项目中的 source.extension.vsixmanifest 文件中配置 VSIX 包。 通过生成解决方案，然后创建 VSIX 包。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要配置并创建 VSIX 包  
  
1.  在**解决方案资源管理器**下**UpgradeDeploymentStep**项目中，打开快捷菜单**source.extension.vsixmanifest**文件，然后依次**打开**。  
  
     Visual Studio 将在清单编辑器中打开该文件。 Source.extension.vsixmanifest 文件是所有的 VSIX 包需要 extension.vsixmanifest 文件的基础。 有关此文件的详细信息，请参阅[VSIX 扩展架构 1.0 引用](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**产品名称**框中，输入**升级用于 SharePoint 项目的部署步骤**。  
  
3.  在**作者**框中，输入**Contoso**。  
  
4.  在**说明**框中，输入**提供可以在 SharePoint 项目中使用的自定义升级部署步骤**。  
  
5.  在**资产**选项卡的编辑器中，选择**新建**按钮。  
  
     **添加新资产**对话框随即出现。  
  
6.  在**类型**列表中，选择**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  此值对应于`MefComponent`extension.vsixmanifest 文件中的元素。 此元素指定的 VSIX 包中的扩展程序集的名称。 有关详细信息，请参阅[MEFComponent 元素 （VSX 架构）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
7.  在**源**列表中，选择**当前解决方案中的项目**。  
  
8.  在**项目**列表中，选择**DeploymentStepExtension**，然后选择**确定**按钮。  
  
9. 在清单编辑器中，选择**新建**再次按钮。  
  
     **添加新资产**对话框随即出现。  
  
10. 在**类型**列表中，输入**SharePoint.Commands.v4**。  
  
    > [!NOTE]  
    >  此元素指定你想要包含在 Visual Studio 扩展中的自定义扩展。 有关详细信息，请参阅[资产元素 （VSX 架构）](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
11. 在**源**列表中，选择**当前解决方案中的项目**。  
  
12. 在**项目**列表中，选择**SharePointCommands**，然后选择**确定**按钮。  
  
13. 在菜单栏上，选择**生成**，**生成解决方案**，并确保解决方案在编译时没有错误。  
  
14. 请确保 UpgradeDeploymentStep 项目的生成输出文件夹现在包含 UpgradeDeploymentStep.vsix 文件。  
  
     默认情况下，生成输出文件夹是...在包含你的项目文件的文件夹下的 \bin\Debug 文件夹。  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>准备测试升级部署步骤  
 若要测试升级部署步骤，必须首先将示例解决方案部署到 SharePoint 站点。 从调试的 Visual Studio 实验实例中的扩展开始。 然后创建一个列表定义和列表实例要用于测试了部署步骤，以及然后将它们部署到 SharePoint 站点。 接下来，修改列表定义和列表实例，并将它们来演示默认部署过程将 SharePoint 站点上的解决方案的覆盖重新部署。  
  
 稍后在本演练中，你将修改的列表定义和列表实例，然后你将升级它们在 SharePoint 站点上。  
  
#### <a name="to-start-debugging-the-extension"></a>若要开始调试扩展  
  
1.  使用管理凭据，重新启动 Visual Studio，然后打开 UpgradeDeploymentStep 解决方案。  
  
2.  在 DeploymentStepExtension 项目中，打开 UpgradeStep 代码文件中，并将断点添加到代码中的第一行`CanExecute`和`Execute`方法。  
  
3.  开始调试通过选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
4.  Visual Studio 将为 SharePoint Projects\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 部署步骤安装扩展，并启动 Visual Studio 的实验实例。 你将在 Visual Studio 的此实例中测试升级部署步骤。  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>若要使用列表定义和列表实例中创建 SharePoint 项目  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  在**新项目**对话框框中，展开**Visual C#**节点或**Visual Basic**节点，展开**SharePoint**节点，然后选择**2010年**节点。  
  
3.  在对话框中的顶部，请确保**.NET Framework 3.5**出现在列表的.NET Framework 的版本。  
  
     为项目[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]和[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]需要此版本的.NET Framework。  
  
4.  在项目模板列表中，选择**SharePoint 2010 项目**，命名该项目**EmployeesListDefinition**，然后选择**确定**按钮。  
  
5.  在**SharePoint 自定义向导**，输入你想要用于调试的站点的 URL。  
  
6.  下**此 SharePoint 解决方案的信任级别是什么**，选择**部署为场解决方案**选项按钮。  
  
    > [!NOTE]  
    >  升级部署步骤不支持沙盒解决方案。  
  
7.  选择**完成**按钮。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]创建 EmployeesListDefinition 项目。  
  
8.  打开 EmployeesListDefinition 项目的快捷菜单，选择**添加**，然后选择**新项**。  
  
9. 在**添加新项-EmployeesListDefinition**对话框框中，展开**SharePoint**节点，然后选择**2010年**节点。  
  
10. 选择**列表**项模板，该项**员工列表**，然后选择**添加**按钮。  
  
     出现 SharePoint 自定义向导  
  
11. 上**选择列表设置**页上，验证以下设置，，然后选择**完成**按钮：  
  
    1.  **员工列表**出现在**你想要列表的显示名称？**框。  
  
    2.  **创建基于自定义的列表：**选择选项按钮。  
  
    3.  **默认值 （空）**中选择**创建基于自定义的列表：**列表。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]创建员工列表项的标题列与单个空实例并打开列表设计器。  
  
12. 在列表设计器中上,**列**选项卡上，选择**键入一个新的或现有的列名称**行，并将中的以下列**列显示名称**列表：  
  
    1.  名字  
  
    2.  公司  
  
    3.  商务电话  
  
    4.  电子邮件  
  
13. 保存所有文件，然后关闭列表设计器。  
  
14. 在**解决方案资源管理器**，展开**员工列表**节点，然后展开**员工列表实例**子节点。  
  
15. 在 Elements.xml 文件中，用下列 XML 替换默认的此文件中的 XML。 此 XML 更改到列表的名称**员工**并添加了命名荣的员工的信息。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
17. 打开 EmployeesListDefinition 项目的快捷菜单，然后选择**打开**或**属性**。  
  
     属性设计器随即打开。  
  
18. 上**SharePoint**选项卡上，清除**调试后自动收回**复选框，，然后将保存属性。  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>若要部署的列表定义和列表实例  
  
1.  在**解决方案资源管理器**，选择**EmployeesListDefinition**项目节点。  
  
2.  在**属性**窗口中，请确保**活动部署配置**属性设置为**默认**。  
  
3.  选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
4.  验证成功生成项目，web 浏览器打开到 SharePoint 站点，**列出**快速启动栏中的项包括新**员工**列表，并能够**员工**列表包括有关荣条目。  
  
5.  关闭 web 浏览器。  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>若要修改的列表定义和列表实例，并将其重新部署  
  
1.  在 EmployeesListDefinition 项目中，打开的子级的 Elements.xml 文件**员工列表实例**项目项。  
  
2.  删除`Data`元素，并从列表中删除有关荣条目其子级。  
  
     完成后，该文件应包含以下 XML。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
4.  打开的快捷菜单**员工列表**项、 项目，然后选择**打开**或**属性**。  
  
5.  在列表设计器中，选择**视图**选项卡。  
  
6.  在**所选列**列表中，选择**附件**，然后选择 < 键能够移到该列**可用列**列表。  
  
7.  重复上述步骤将**商务电话**列从**所选列**列表到**可用列**列表。  
  
     此操作将删除这些字段的默认视图从**员工**SharePoint 站点上的列表。  
  
8.  开始调试通过选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
9. 验证**部署冲突**对话框随即出现。  
  
     此对话框中显示到已向其部署该解决方案的 SharePoint 站点时 Visual Studio 尝试部署解决方案 （列表实例）。 在本演练中执行升级部署步骤更高版本时，不会出现此对话框。  
  
10. 在**部署冲突**对话框框中，选择**自动解决**选项按钮。  
  
     Visual Studio 删除 SharePoint 站点上的列表实例，部署在项目中，该列表项目，然后打开 SharePoint 站点。  
  
11. 在**列出**部分的快速启动栏中，选择**员工**列表，并验证以下详细信息：  
  
    -   **附件**和**住宅电话号码**列不会显示在此视图的列表。  
  
    -   列表为空。 使用时**默认**要重新部署该解决方案，部署配置**员工**列表已替换为你的项目中的新的空列表。  
  
## <a name="testing-the-deployment-step"></a>测试部署步骤  
 现在你就可以测试升级部署步骤。 首先，将项添加到 SharePoint 中的列表实例。 然后将更改的列表定义和列表实例，将它们升级在 SharePoint 站点上，并确认升级部署步骤不会覆盖新项。  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>若要手动向列表添加项  
  
1.  在 SharePoint 站点上，功能区中下**列表工具**选项卡上，选择**项**选项卡。  
  
2.  在**新建**组中，选择**新项**。  
  
     作为替代方法，你可以选择**添加新项**项列表自身中的链接。  
  
3.  在**员工-新项**窗口，请在**标题**框中，输入**设施 Manager**。  
  
4.  在**名字**框中，输入**Andy**。  
  
5.  在**公司**框中，键入**Contoso**。  
  
6.  选择**保存**按钮，验证在列表中，将出现新项，然后关闭 web 浏览器。  
  
     稍后在本演练中，你将使用此项以验证升级部署步骤不会覆盖此列表的内容。  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>若要测试升级部署步骤  
  
1.  在实验实例中的 Visual Studio 中，在**解决方案资源管理器**，打开快捷菜单**EmployeesListDefinition**项目节点，，然后选择**属性**.  
  
     属性编辑器/Designer 随即打开。  
  
2.  上**SharePoint**选项卡上，设置**活动部署配置**属性**升级**。  
  
     此自定义部署配置包括在新的升级部署步骤。  
  
3.  打开的快捷菜单**员工列表**项、 项目，然后选择**属性**或**打开**。  
  
     属性编辑器/Designer 随即打开。  
  
4.  上**视图**选项卡上，选择**电子邮件**列，然后选择 **<** 键能够移从该列**所选列**列表到**可用列**列表。  
  
     此操作将删除这些字段的默认视图从**员工**SharePoint 站点上的列表。  
  
5.  开始调试通过选择 F5 键，或在菜单栏上，选择**调试**，**启动调试**。  
  
6.  验证在 Visual Studio 的其他实例中在代码停止在更早版本中设置的断点处`CanExecute`方法。  
  
7.  再次选择 F5 键，或在菜单栏上，选择**调试**，**继续**。  
  
8.  验证在代码中设置的断点上停止`Execute`方法。  
  
9. 选择 F5 键，或在菜单栏上，选择**调试**，**继续**最后一次。  
  
     Web 浏览器打开 SharePoint 站点。  
  
10. 在**列出**部分的快速启动区域中，选择**员工**列表，并验证以下详细信息：  
  
    -   手动添加更早版本 （对于 Andy，设施 manager) 的项所做的列表。  
  
    -   **商务电话**和**电子邮件地址**列不会显示在此视图的列表。  
  
     **升级**部署配置修改现有**员工**SharePoint 站点上的列表实例。 如果你使用**默认**部署配置而不是**升级**配置，则会遇到部署冲突。 Visual Studio 将通过替换来解决该冲突**员工**列表中，并为 Andy，设备管理器的项将被删除。  
  
## <a name="cleaning-up-the-development-computer"></a>清理开发计算机  
 完成测试升级部署步骤后，从 SharePoint 站点中删除列表实例和列表定义和从 Visual Studio 中删除部署步骤扩展。  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>若要从 SharePoint 站点中删除列表实例  
  
1.  打开**员工**列出在 SharePoint 站点上，如果尚未打开列表。  
  
2.  在功能区中的 SharePoint 站点上，选择**列表工具**选项卡上，然后选择**列表**选项卡。  
  
3.  在**设置**组中，选择**列表设置**项。  
  
4.  下**权限和管理**，选择**删除此列表**命令中，选择**确定**以确认你要将此列表发送到回收站，然后关闭 web浏览器。  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>若要从 SharePoint 站点中删除该列表定义  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**生成**，**收回**。  
  
     Visual Studio 将收回从 SharePoint 站点的列表定义。  
  
#### <a name="to-uninstall-the-extension"></a>卸载扩展  
  
1.  在实验实例中的 Visual Studio 中，在菜单栏上，选择**工具**，**扩展和更新**。  
  
     此时，“扩展和更新”对话框打开。  
  
2.  在扩展的列表中，选择**升级用于 SharePoint 项目的部署步骤**，然后选择**卸载**命令。  
  
3.  在显示的对话框中，选择**是**以确认你要卸载扩展，然后选择**立即重新启动**要完成卸载。  
  
4.  关闭 Visual Studio （实验实例和 UpgradeDeploymentStep 解决方案处于打开状态的 Visual Studio 的实例） 的两个实例。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  