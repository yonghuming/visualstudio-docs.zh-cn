---
title: "演练：使用设计器为 SharePoint 创建 Web 部件"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 创建"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 设计器"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 设计"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 演练：使用设计器为 SharePoint 创建 Web 部件
  如果为 SharePoint 站点创建 Web 部件，则用户可使用浏览器直接修改该站点上页面的内容、外观和行为。  本演练演示如何使用 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中 SharePoint 的“可视 Web 部件”项目模板以可视化方式创建 Web 部件。  
  
 您将创建的 Web 部件显示月历视图以及与站点上的每个日历列表相对应的复选框。  用户可以通过选中这些复选框来指定要包括在月历视图中的日历列表。  
  
 本演练阐释了以下任务：  
  
-   使用“可视 Web 部件”项目模板创建 Web 部件。  
  
-   使用 Visual Studio 中的 Visual Web Developer 设计器设计 Web 部件。  
  
-   添加代码以处理 Web 部件上的控件事件。  
  
-   在 SharePoint 中测试 Web 部件。  
  
    > [!NOTE]  
    >  以下说明中的某些 Visual Studio 用户界面元素在您的计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   支持的 Windows 和 SharePoint 版本。  请参见 [开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] 或更高级的版本。  
  
## 创建 Web 部件项目  
 首先，使用“可视 Web 部件”项目模板创建 web 部件项目。  
  
#### 创建可视 Web 部件项目  
  
1.  使用**“以管理员身份运行”**选项启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
     此时将出现“新建项目”对话框。  
  
3.  在“新建项目”对话框中，在“Visual C\#”或“Visual Basic”下，展开“Office\/SharePoint”，然后选择“SharePoint 解决方案”类别。  
  
4.  在模板列表中，选择“SharePoint 2013 \- 可视 Web 部件”模板，然后选择“确定”按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  使用此向导可以指定用于调试项目的站点以及解决方案的信任级别。  
  
5.  在“此 SharePoint 解决方案的信任级别是什么?”部分中，选中“部署为场解决方案”选项按钮。  
  
6.  选择“完成”按钮接受默认的本地 SharePoint 站点。  
  
## 设计 Web 部件  
 通过将控件从“工具箱”添加到 Visual Web Developer 设计器的图面上来设计 Web 部件。  
  
#### 设计 Web 部件的布局  
  
1.  在 Visual Web Developer 设计器上，选择“设计”选项卡以切换到设计视图。  
  
2.  在菜单栏上，依次选择“查看”、“工具箱”。  
  
3.  在“工具箱”的“标准”节点中，选择“CheckBoxList”控件，然后执行以下步骤之一：  
  
    -   打开“CheckBoxList”控件的快捷菜单，选择“复制”，打开设计器中第一行的快捷菜单，然后选择“粘贴”。  
  
    -   从“工具箱”拖动“CheckBoxList”控件，并将其连接到设计器的第一行。  
  
4.  重复上面的步骤，但将按钮移至设计器的下一行。  
  
5.  在设计器中，选择“Button1”按钮。  
  
6.  在菜单栏上，选择**“视图”**，**“属性窗口”**。  
  
     这将打开**“属性”**窗口。  
  
7.  在按钮的“文本”属性中，输入 Update。  
  
## 处理 Web 部件上的控件事件  
 添加可用于将日历添加到母版日历视图中的代码。  
  
#### 处理 Web 部件上的控件事件  
  
1.  执行下面的某一组步骤：  
  
    -   在设计器中，双击“更新”按钮。  
  
    -   在“更新”按钮的“属性”窗口中，选择“事件”按钮。  在“Click”属性中，输入 **Button1\_Click**，然后选择 Enter 键。  
  
     用户控件代码文件随即在代码编辑器中打开，并显示 `Button1_Click` 事件处理程序。  然后，您需要向此事件处理程序添加代码。  
  
2.  将以下语句添加到用户控件代码文件的顶部。  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  将以下代码行添加到 `VisualWebPart1` 类中。  此代码声明一个月历视图控件。  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  用以下代码替换 `VisualWebPart1` 类的 `Page_Load` 方法。  这段代码执行下列任务：  
  
    -   向用户控件添加月历视图。  
  
    -   在网站上为每个日历列表添加一个复选框。  
  
    -   指定在日历视图中显示的每种项的模板。  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  用以下代码替换 `VisualWebPart1` 类的 `Button1_Click` 方法。  此代码将各个所选日历中的项添加到母版日历视图中。  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## 测试 Web 部件  
 在运行项目时，SharePoint 网站将打开。  Web 部件会自动添加到 SharePoint 中的 Web 部件库中。  若要测试此项目，请执行以下任务：  
  
-   为两个单独的日历列表中的每个列表分别添加一个事件。  
  
-   将 Web 部件添加到 Web 部件页。  
  
-   指定要包含在月历视图中的列表。  
  
#### 向网站上的日历列表添加事件  
  
1.  在 Visual Studio 中，选择 F5 键。  
  
     SharePoint 站点打开，并在该页上显示 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 快速启动栏。  
  
2.  在快速启动栏上，在“列表”下，选择“日历”链接。  
  
     此时将显示**“日历”**页。  
  
     如果没有日历链接显示在快速启动栏中，则选择“网站内容”链接。  如果站点内容页不显示“日历”项目，请创建一个。  
  
3.  在日历页上，选择日期，然后在选定的日期中选择“添加”链接添加事件。  
  
4.  在“标题”框中的默认日历中输入“事件”，然后选中“保存”按钮。  
  
5.  选择“站点内容”链接，然后选择“添加应用”图块。  
  
6.  在“创建”页上，选择“日历”类型，命名日历，然后选择“创建”按钮。  
  
7.  将事件添加到新日历，在自定义日历中将其命名为“事件”，然后选择“保存”按钮。  
  
#### 将 Web 部件添加到 Web 部件页  
  
1.  在“站点内容”页，打开“站点页面”文件夹。  
  
2.  在功能区中，选择“文件”选项卡，打开“新建文档”菜单，然后选择“Web 部件页”命令。  
  
3.  在“新建 Web 部件页”页上，将该页命名为**“SampleWebPartPage.aspx”**，然后选中“创建”按钮。  
  
     此时将显示 Web 部件页。  
  
4.  在 Web 部件页的顶部区域，选择“插入”选项卡，然后选择“Web 部件”按钮。  
  
5.  依次选择“自定义”文件夹、“VisualWebPart1”Web 部件，然后选中“添加”按钮。  
  
     此时将在该页上显示 Web 部件。  此时将在 Web 部件上显示以下控件：  
  
    -   月历视图。  
  
    -   **“更新”**按钮。  
  
    -   **“日历”**复选框。  
  
    -   “自定义日历”复选框。  
  
#### 指定要包含在月历视图中的列表  
  
1.  在 Web 部件中，指定要包含在月历视图中的日历，然后选中“更新”按钮。  
  
     此时会在月历视图中显示所有选定日历的事件。  
  
## 请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  