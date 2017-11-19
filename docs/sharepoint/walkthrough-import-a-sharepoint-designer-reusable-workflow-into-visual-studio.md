---
title: "演练： 将 SharePoint Designer 可重用工作流导入 Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: da498bd8b6b19670b98c2e0a8f84c1a0bff4b40d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>演练：将 SharePoint Designer 可重用工作流导入 Visual Studio
  本演练演示如何导入到的 SharePoint Designer 2010 中创建的可重用工作流[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 工作流项目。  
  
 在 SharePoint Designer 中创建的工作流或*声明性工作流*，组成[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]语句而不是代码。 SharePoint Designer 2010 引入了*可重用工作流*，这是可移植的声明性工作流，可由 SharePoint 站点中的不同列表。  
  
 在中创建的工作流[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]，例如顺序和状态机工作流称为*代码工作流*。 代码工作流由 XML 文件和在其中用户可以自定义工作流的行为的代码模块组成。  
  
 Visual Studio 允许您在 SharePoint Designer 2010 中导入可重用工作流，并将其转换为代码工作流，以便在 SharePoint 网站中使用。  
  
 本演练演示了下列任务：  
  
-   在 SharePoint Designer 中创建简单的可重用工作流。  
  
-   导出 SharePoint Designer 可重用工作流，到.wsp 文件和 sharepoint。  
  
-   导入.wsp 文件到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用导入可重用工作流项目。  
  
-   通过将代码添加更改工作流。  
  
-   在 SharePoint 站点中使用导入工作流。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## <a name="create-target-sharepoint-subsites"></a>创建目标 SharePoint 子站点  
 首先创建两个新的 SharePoint 子站点： 一个用于承载从 SharePoint Designer 中，另一个用来承载转换后的工作流的可重用工作流。  
  
#### <a name="to-create-sharepoint-subsites"></a>若要创建 SharePoint 子站点  
  
1.  在 SharePoint Designer 2010，在菜单栏上，选择**文件**，**新建空白网站**。  
  
2.  在**新建空白网站**对话框中，浏览到 SharePoint 站点，你想要创建工作流，或使用 http:// 值*系统名称*/，然后选择**确定**按钮。  
  
     随后显示该主页。  
  
3.  在**子站点**部分中，选择**新建**按钮。  
  
4.  在**新建**对话框框中，选择**SharePoint 模板**从列表中的左窗格中，选择**团队站点**从右窗格中列表。  
  
5.  在**指定网站位置**框中，替换的单词**子站点**将 URL 中**SPD1**，然后选择**确定**按钮。  
  
     这将打开 SharePoint 设计器中新的子站点。 关闭此实例的 SharePoint 设计器，然后返回到第一个实例 （顶层站点）。  
  
6.  重复步骤 3-5 以创建第二个子网站，此时替换单词**子站点**中[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]与**SPD2**。  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>创建 SharePoint Designer 可重用工作流  
 因为 SharePoint 中不包含任何可用于此示例的可重用工作流，则将创建一个。 此简单的工作流，用户具有特定标题的任务列表中输入新任务的任务分配给该用户。  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>若要创建 SharePoint Designer 可重用工作流  
  
1.  在**子站点**部分中，选择**SPD1**站点以进行修改。  
  
2.  在功能区中，选择**可重用工作流**按钮。  
  
     将出现创建可重用工作流向导。  
  
3.  在**名称**框中，输入**SPD 任务工作流**。  
  
4.  在**内容类型**列表中，选择**任务**，然后选择**确定**按钮。  
  
     在 SharePoint Designer 工作流设计器中打开工作流。  
  
5.  在工作流设计器中，选择步骤 1，然后在功能区中，选择**条件**按钮。  
  
6.  在条件列表中，选择**如果当前项字段等于值**。  
  
     此步骤将添加名为的条件**如果字段等于值**。  
  
7.  在**如果字段等于值**条件中，选择**字段**链接。  
  
8.  在值列表中，选择**标题**。  
  
9. 在**如果字段等于值**条件中，选择**值**链接。  
  
10. 在框中，输入**新任务**。  
  
     条件语句现在显示为**如果当前项： 标题等于新任务**。  
  
11. 选择条件语句中，下面的行，然后，在功能区中，选择**操作**按钮。  
  
12. 在操作的列表中，选择**中当前项的组字段**。  
  
13. 在**集字段值**操作，选择**字段**链接，然后，在列表中，选择**分配给**。  
  
14. 在**集字段值**操作，选择**值**链接，然后，在现有的用户和组的列表中，选择**创建项的用户**。  
  
15. 选择**添加**按钮，，然后选择**确定**按钮。  
  
     操作语句现在显示为**设置分配对象设置为当前项目： 创建者**。  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>保存和部署可重用工作流  
 因为[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可以导入.wsp 文件，则必须将可重用工作流另存为.wsp 文件并导入到之前将其部署到 SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
> [!IMPORTANT]  
>  如果收到运行时错误，执行以下过程，你必须能够访问 SharePoint 站点的系统上执行过程。  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>若要保存和部署可重用工作流  
  
1.  在 SharePoint Designer 顶部，选择**保存**按钮以保存你的进度，，然后选择**发布**按钮以部署工作流保存到**SPD1** SharePoint 站点.  
  
2.  在导航窗格中，选择**工作流**对象。  
  
3.  下**可重用工作流**，选择**SPD 任务工作流**。  
  
4.  在功能区中，选择**另存为模板**按钮以将工作流另存为.wsp 文件。  
  
5.  打开**SPD1**要在 SharePoint 中查看.wsp 文件浏览器中的 SharePoint 站点。  
  
6.  在快速启动栏上，选择**库**链接。  
  
7.  在**文档库**部分中，选择**站点资产**链接。  
  
     **SPD 任务工作流**文件与其他站点资产一起列出。  
  
8.  在文件列表中，选择该文件的名称  
  
9. 在**文件下载**对话框框中，选择**保存**按钮以保存您的本地系统上的.wsp 文件。  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>.Wsp 文件导入 Visual Studio  
 .Wsp 文件导入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用的导入可重用工作流项目。 此项目将可重用的声明性工作流从工作流转换为代码工作流中。 转换工作流后，你将使用代码修改其行为。  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>若要从.wsp 文件中导入工作流，并对其进行修改  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在菜单栏上，选择**文件**，**新建**，**项目**。  
  
2.  在**新项目**对话框框中，展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**节点。  
  
3.  在**模板**窗格中，选择**导入可重用 SharePoint 2010 工作流**模板，将作为项目的名称**WorkflowImportProject1**，然后选择**确定**按钮。  
  
     将出现 SharePoint 自定义向导。  
  
4.  上**指定用于调试的站点和安全性级别**页上，输入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]第二个 SharePoint 子站点之前创建： http://*系统名称*/SPD2。  
  
5.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，选择**部署为场解决方案**选项按钮，，然后选择**下一步**按钮。  
  
     有关沙盒的详细信息与场解决方案，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  在**指定新项目源**页上，浏览到你前面保存.wsp 文件的位置在系统上，打开该文件，然后选择**下一步**按钮。  
  
    > [!NOTE]  
    >  选择**完成**按钮导入.wsp 文件中的所有可用项。  
  
     此时将显示可用于导入可重用工作流的列表。  
  
7.  在**选择要导入的项**框中，选择**SPD 任务工作流**工作流，然后选择**完成**按钮。  
  
     在导入操作完成后，项目名称为**WorkflowImportProject1**包含名为工作流创建**SPD_Workflow_TestFT**。 在此文件夹是工作流的定义文件 Elements.xml 和工作流设计器文件 (.xoml)。 该设计器包含两个文件： 规则文件 (.rules) 和代码隐藏文件 （.cs 或.vb，具体取决于你的项目的编程语言）。  
  
8.  在**解决方案资源管理器**，删除**其他已导入文件**文件夹。  
  
9. 在 Elements.xml 文件中，删除 `InstantiationURL="_layouts/IniErkflIP.sspx"`。  
  
10. 在**解决方案资源管理器**，选择**WorkflowImportProject1**，然后在菜单栏上，选择**项目**，**设为启动项目**到设置**WorkflowImportProject1**为启动项目。  
  
     立即在调试项目时，这会显示的列表。  
  
11. 因为**导入可重用 SharePoint 2010 工作流**模板不能导入的导入工作流的关联属性值，则你必须输入它们。 具体方法为：  
  
    1.  在**解决方案资源管理器**，选择**SPD_Workflow_TestFT**节点。  
  
    2.  选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")) 旁的一个列表属性，如按钮**目标列表**属性。  
  
    3.  填写 SharePoint 自定义向导中的缺失值，然后选择**完成**按钮。  
  
12. 选择.xoml 文件，然后，在菜单栏上，选择**视图**，**设计器**若要在工作流设计器中查看导入工作流。  
  
13. 在**Windows Workflow v3.0**节点**工具箱**，执行以下步骤之一：  
  
    -   打开的快捷菜单**代码**活动，然后选择**复制**。 在工作流设计器中，打开的行的快捷菜单**SequenceActivity1**活动，然后选择**粘贴**。  
  
    -   拖动**代码**活动从**工具箱**到工作流设计器，并将其连接到下一行**SequenceActivity1**活动。  
  
     这将活动添加到名为工作流设计器**CodeActivity1**。 在此活动中，你将添加在通知列表中创建公告，当用户启动工作流的代码操作。  
  
14. 执行下面的某一组步骤：  
  
    -   双击**CodeActivity1**生成事件处理程序并查看代码。  
  
    -   在**属性**窗口**CodeActivity1**，设置的值**ExecuteCode**属性**codeActivity_ExecuteCode**。  
  
15. 现有下添加以下**使用**或**导入**语句：  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 替换`codeActivity1_ExecuteCode`替换为以下：  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>部署项目并将关联的工作流  
 接下来，运行 WorkflowImportProject1 将其部署到 SharePoint 站点，然后将该工作流关联的任务列表，查看和测试修改后，转换工作流。  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>若要部署项目并将关联的工作流  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，选择 F5 以运行和部署转换的工作流项目。  
  
2.  在快速启动栏上，选择**任务**链接以显示任务列表。  
  
3.  上**列表工具**选项卡上，选择**项**按钮，，然后选择**新项**按钮。  
  
     **任务-新项**对话框随即打开。  
  
4.  在**标题**框中，输入**新任务**，然后选择**保存**按钮。  
  
5.  上**列表工具**选项卡上，选择**列表**按钮，，然后选择**列表设置**按钮。  
  
     **列表设置**页将出现。  
  
6.  在**权限和管理**部分中，选择**工作流设置**链接。  
  
     **工作流设置**页将出现。  
  
7.  选择**添加工作流**链接。  
  
8.  在**工作流**列表中，选择**WorkflowImportProject1-SPD 工作流测试**。  
  
9. 在**名称**框中，输入**SPD 工作流测试**，然后选择**确定**按钮。  
  
10. 在快速启动栏上，选择**任务**列表。  
  
11. 选择箭头旁边**新任务**，然后在列表中，选择**工作流**。  
  
12. 在**启动新工作流**部分中，选择的链接**SPD 工作流测试**，然后选择**启动**按钮以启动工作流。  
  
    > [!NOTE]  
    >  或者，你可以自动将工作流的列表通过运行工作流设置向导并设置工作流以自动关联。  
  
     请注意，由工作流执行两项操作： 在任务中的显示您的姓名**指派给**列中和公告将出现在**公告**列表。  
  
## <a name="see-also"></a>另请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  