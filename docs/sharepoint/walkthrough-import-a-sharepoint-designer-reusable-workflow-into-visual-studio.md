---
title: "演练：将 SharePoint Designer 可重用工作流导入 Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发，导入可重用工作流"
  - "可重用工作流 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# 演练：将 SharePoint Designer 可重用工作流导入 Visual Studio
  本演练演示如何将 SharePoint Designer 2010 中创建的可重用工作流导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 工作流项目中。  
  
 在 SharePoint Designer 中创建的工作流（即，声明性工作流）由 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 语句组成，而非由代码组成。  SharePoint Designer 2010 引入了可重用工作流，它们是可由 SharePoint 站点中的不同列表使用的可移植的声明性工作流。  
  
 工作流在[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]中创建，如顺序工作流和状态机工作流，称为“代码工作流”。  代码工作流由 XML 文件和代码模块组成，用户可以在这些文件和模块中自定义工作流的行为。  
  
 Visual Studio允许您可以在 SharePoint Designer 2010 中导入可重用工作流，并将其转换为代码工作流，以便在 SharePoint 站点中使用。  
  
 本演练将演示以下任务：  
  
-   在 SharePoint Designer 中创建一个简单的可重用工作流。  
  
-   将 SharePoint Designer 可重用工作流导出到一个 .wsp 文件中，然后再将其导入到 SharePoint 中。  
  
-   使用“导入可重用工作流”项目将 .wsp 文件导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  
  
-   通过添加代码修改工作流。  
  
-   在 SharePoint 站点中使用导入的工作流。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## 创建目标 SharePoint 子站点  
 首先创建两个新的 SharePoint 子站点：一个用于承载来自 SharePoint Designer 的可重用工作流，另一个用于承载转换后的工作流。  
  
#### 创建 SharePoint 子站点  
  
1.  在 SharePoint Designer 2010，请在菜单栏上，依次选择 **文件**，**新建空白网站**。  
  
2.  在**“新建空站点”**对话框中，浏览至要在其中创建工作流的 SharePoint 站点，或者使用默认值 http:\/\/*SystemName*\/，然后选择“确定”按钮。  
  
     此时将显示主页。  
  
3.  在 **子网站** 部分中，选择 **新建** 按钮。  
  
4.  在 **新建** 对话框中，从左侧窗格中的列表选择 **SharePoint 模板**，然后从右窗格的列表中选择 **工作组网站**。  
  
5.  在**“指定您的网站位置”**框中，用 SPD1 替换 URL 中的**“subsite”**一词，然后选择**“确定”**按钮。  
  
     这将在 SharePoint Designer 中打开新的子站点。  关闭此 SharePoint Designer 实例并返回到第一个实例（首要站点）。  
  
6.  重复步骤 3 至步骤 5 以创建第二个子站点，这次将用 SPD2 替换 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 中的**“subsite”**一词。  
  
## 创建 SharePoint Designer 可重用工作流  
 由于 SharePoint 不包括可用于此示例的任何可重用工作流，因此您将创建一个可重用工作流。  在此简单工作流中，当某个用户在“任务”列表中输入某个具有特定标题的新任务时，将向该用户分配此任务。  
  
#### 创建 SharePoint Designer 可重用工作流  
  
1.  在“子网站”部分，选择**SPD1**网站修饰。  
  
2.  在功能区上，选择 **可重用工作流** 按钮。  
  
     将出现“创建可重用工作流”向导。  
  
3.  在**“名称”**框中，键入“SPD 任务工作流”。  
  
4.  在**“内容类型”**列表中，选择**“任务”**，然后选择**“确定”**按钮。  
  
     该工作流将在 SharePoint Designer 工作流设计器中打开。  
  
5.  在工作流设计器中，选择功能区上的步骤 1，然后，选择 **条件** 按钮。  
  
6.  在环境列表中，选择 **如果当前项目域等于值**。  
  
     此步骤添加名为 **如果字段设置为相等的值**的条件。  
  
7.  在**“如果字段等于值”**条件中，选择**“字段”**链接。  
  
8.  在值的列表中，选择**“标题”**。  
  
9. 在**“如果字段等于值”**条件中，选择**“值”**链接。  
  
10. 在框中输入“新任务”。  
  
     条件语句现在显示为**“如果当前项:标题等于新任务”**。  
  
11. 选择条件语句下面的行，然后，在功能区上，选择 **操作** 按钮。  
  
12. 在操作列表中，选择 **设置当前项目中的域**。  
  
13. 在**“将字段设置为值”**操作中，选择**“字段”**链接，然后在列表中选择**“分配对象”**。  
  
14. 在 **设置字段值** 操作，请选择 **值**链接，然后在现有的用户列表和组中，选择 **创建项的用户**。  
  
15. 选择**“添加”**按钮，然后选择**“确定”**按钮。  
  
     操作语句现在显示为**“将分配对象设置为当前项目:创建者”**。  
  
## 保存并部署可重用工作流  
 由于 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只能导入 .wsp 文件，因此必须先将可重用工作流另存为 .wsp 文件，并将其部署到 SharePoint，然后才能将其导入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  
  
> [!IMPORTANT]  
>  如果您在执行以下过程时接收到运行时错误，则必须在具有对 SharePoint 网站的访问权的系统上执行该过程。  
  
#### 保存并部署可重用工作流  
  
1.  在 SharePoint Designer 顶部，选择**“保存”**按钮，保存您的进度，然后选择**“发布”**按钮将工作流部署到 SharePoint 站点**“SPD1”**。  
  
2.  在导航窗格中，选择 **工作流** 对象。  
  
3.  在 **可重用工作流**,选择**SPD 任务工作流**.  
  
4.  在功能区中，选择**“另存为模板”**按钮，以将工作流另存为 .wsp 文件。  
  
5.  在浏览器中，打开**“SPD1”**SharePoint 站点，查看 SharePoint 中的 .wsp 文件。  
  
6.  在快速启动栏上，选择 **库** 链接。  
  
7.  在**“文档库”**部分中，选择**“站点资产”**链接。  
  
     **“SPD 任务工作流”**文件将与其他站点资产一起列出。  
  
8.  在文件列表中，选中该文件名称  
  
9. 在**“文件下载”**对话框中，选择**“保存”**按钮，将 .wsp 文件保存到您的本地系统上。  
  
## 将 .wsp 文件导入到 Visual Studio 中  
 使用“导入可重用工作流”项目将 .wsp 文件导入到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中。  此项目将工作流从一个可重用的声明性工作流转换为一个代码工作流。  转换工作流之后，您将使用代码来修改其行为。  
  
#### 从 .wsp 文件导入工作流并进行修改  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]菜单栏上，依次选择**文件**、**新建**, **项目**。  
  
2.  在**“新建项目”**对话框中，在**“Visual C\#”**或**Visual Basic**下，展开**SharePoint**节点，然后选择**2010**节点。  
  
3.  在 **模板** 窗格中，选择 **导入可重用 SharePoint 2010 工作流** 模板，保留项目的名称为 **WorkflowImportProject1**，再选择 **确定** 按钮。  
  
     这将显示“SharePoint 自定义向导”。  
  
4.  在**“指定用于调试的站点和安全级别”**页上，为您先前创建的第二个 SharePoint 子站点输入 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]：http:\/\/*system name*\/SPD2。  
  
5.  在“此 SharePoint 解决方案的信任级别是什么?”部分中，选中“部署为场解决方案”选项按钮，然后选择**下一步**按钮。  
  
     有关沙盒化解决方案与场解决方案的更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  在**“指定新项目源”**页上，浏览到系统上您先前保存 .wsp 文件的位置，打开文件，然后选择**“下一步”**按钮。  
  
    > [!NOTE]  
    >  选择 **完成** 按钮导入 .wsp 文件中的所有可用项。  
  
     这将显示可导入的可重用工作流的列表。  
  
7.  在**“选择要导入的项”**框中，选择工作流**“SPD 任务工作流”**，然后选择**“完成”**按钮。  
  
     完成导入操作后，将创建一个名为**“WorkflowImportProject1”**的项目，其中包含一个名为**“SPD\_Workflow\_TestFT”**的工作流。  此文件夹中包含工作流的定义文件 Elements.xml 和工作流设计器文件 \(.xoml\)。  该设计器中包含两个文件：规则文件 \(.rules\) 和代码隐藏文件（.cs 或 .vb，具体取决于项目的编程语言）。  
  
8.  在 **解决方案资源管理器**中，请删除 **导入的其他文件** 文件夹。  
  
9. 在 Elements.xml 文件中，删除 `InstantiationURL="_layouts/IniErkflIP.sspx"`。  
  
10. 在 **解决方案资源管理器**中，选择 **WorkflowImportProject1**，在菜单栏上，选择 **项目**，**设为启动项目** 设置 **WorkflowImportProject1** 为启动项。  
  
     这将在调试项目时立即显示列表。  
  
11. 由于**“导入可重用SharePoint 2010 工作流”**模板不能导入已导入的工作流的关联属性值，因此您必须输入这些值。  具体方法为：  
  
    1.  在**“解决方案资源管理器”**中，选择**“SPD 工作流TestFT”**节点。  
  
    2.  选择某个列表属性旁边选择省略号 \(![ASP.NET 移动设计器中的省略号](~/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\) 按钮，如 **目标列表** 属性。  
  
    3.  在" SharePoint 自定义向导"中填入缺少的值，然后选择 **完成** 按钮。  
  
12. 选择 .xoml 文件，然后，菜单栏上，选择 **视图**，**设计器** 显示在工作流设计器中导入的工作流。  
  
13. 在 **Windows Workflow v3.0工具箱**节点，请执行以下步骤：  
  
    -   打开**代码**活动的快捷菜单，然后选择**“复制”**。  在工作流设计器，打开 **SequenceActivity1** 活动下方的行快捷菜单，然后选择 **粘贴**。  
  
    -   将 **工具箱** 的 **代码** 活动拖拽到工作流设计器，并将其连接到 **SequenceActivity1** 活动下方的行。  
  
     这将在工作流设计器中添加一个名为**“CodeActivity1”**的活动。  在此活动中，您将添加一个代码操作，当用户启动工作流时，该操作会在“公告”列表中创建一个公告。  
  
14. 执行下面的某一组步骤：  
  
    -   双击**“CodeActivity1”**以生成事件处理程序并查看代码。  
  
    -   在 **属性** 窗口 **CodeActivity1**，设置值 **ExecuteCode** 属性为 **codeActivity\_ExecuteCode**。  
  
15. 在现有 **using** 或 **Imports** 语句的下方添加以下内容：  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 用以下内容替换 `codeActivity1_ExecuteCode`：  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## 部署项目并关联工作流  
 接下来，运行 WorkflowImportProject1 以将其部署到 SharePoint 站点，然后将工作流与“任务”列表关联起来，以查看和测试经修改的转换后工作流。  
  
#### 部署项目并关联工作流  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，选择 F5 键以运行和部署转换的工作流项目。  
  
2.  快速启动栏上，选择**“任务”**链接，以显示任务列表。  
  
3.  在 **列表工具** 选项卡，选择 **项** 按钮，然后选择 **新建项** 按钮。  
  
     **“任务 \- 新项”**对话框打开。  
  
4.  在**“标题”**框中，输入新建任务，然后选择**“保存”**按钮。  
  
5.  在 **列表工具** 选项卡，选择 **列表** 按钮，然后选择 **列表设置** 按钮。  
  
     **列表设置** 页出现。  
  
6.  在**“权限和管理”**部分中，选择**“工作流设置”**链接。  
  
     这将出现**“工作流设置”**页。  
  
7.  选择 **添加工作流** 链接。  
  
8.  在**“工作流”**列表中，选择**“WorkflowImportProject1 \- SPD 工作流测试”**。  
  
9. 在**“名称”**框中，输入 SPD 工作流测试，然后选择“确定”按钮。  
  
10. 在快速启动栏上，选择 **任务** 列表。  
  
11. 单击 **新任务**旁边的箭头，然后在列表中，选择 **工作流**。  
  
12. 在**开始一个新的工作流**部分中，选择**SPD 工作流测试**链接，然后选择**开始**按钮以初始化工作流。  
  
    > [!NOTE]  
    >  或者，可以通过运行工作流设置向导并将工作流设置为自动关联，自动将工作流与列表关联起来。  
  
     请注意，工作流将执行两项操作：在任务的**“分配对象”**列中显示您的姓名，并在**“公告”**列表中显示公告。  
  
## 请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  