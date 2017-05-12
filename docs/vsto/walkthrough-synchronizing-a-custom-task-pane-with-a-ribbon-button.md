---
title: "演练：将自定义任务窗格与功能区按钮同步"
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
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]，显示和隐藏"
  - "显示自定义任务窗格"
  - "功能区 [Visual Studio 中的 Office 开发]，自定义任务窗格"
  - "切换按钮 [Visual Studio 中的 Office 开发]"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]，使用功能区按钮进行同步"
  - "用户界面 [Visual Studio 中的 Office 开发]，自定义任务窗格"
  - "同步 [Visual Studio 中的 Office 开发]，自定义任务窗格"
  - "任务窗格 [Visual Studio 中的 Office 开发]，显示和隐藏"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]，创建"
  - "隐藏自定义任务窗格"
  - "任务窗格 [Visual Studio 中的 Office 开发]，创建"
  - "任务窗格 [Visual Studio 中的 Office 开发]，使用功能区按钮进行同步"
ms.assetid: 00ce8b1e-1370-42f2-9dc9-609cada392f1
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 演练：将自定义任务窗格与功能区按钮同步
  本演练演示如何创建用户可以通过单击功能区上的切换按钮进行隐藏或显示的自定义任务窗格。 应始终创建一个可供用户单击以显示或隐藏你的自定义任务窗格的用户界面 \(UI\) 元素，如按钮，因为 Microsoft Office 应用程序不提供用户用于显示或隐藏自定义任务窗格的默认方式。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 虽然本演练具体使用的是 Excel，但其中所阐释的概念同样适用于上面所列的应用程序。  
  
 本演练阐释了以下任务：  
  
-   设计自定义任务窗格的 UI。  
  
-   向功能区添加切换按钮。  
  
-   使用自定义任务窗格同步切换按钮。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel 或 Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]。  
  
## 创建外接程序项目  
 在此步骤中，你将创建 Excel VSTO 外接程序项目。  
  
#### 创建新项目  
  
1.  使用 Excel 外接程序项目模板，创建一个名为 **SynchronizeTaskPaneAndRibbon** 的 Excel 外接程序项目。 有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 打开 **ThisAddIn.cs** 或 **ThisAddIn.vb** 代码文件，并将 **SynchronizeTaskPaneAndRibbon** 项目添加到**“解决方案资源管理器”**。  
  
## 向功能区添加切换按钮  
 Office 应用程序的设计准则之一是：用户应始终能控制 Office 应用程序 UI。 若要让用户可以控制自定义任务窗格，可以添加一个可显示和隐藏任务窗格的功能区切换按钮。 若要创建一个切换按钮，则将**“功能区\(可视化设计器\)”**项添加到项目。 设计器可帮助你添加和放置控件、设置控件属性以及处理控件事件。 有关详细信息，请参阅[功能区设计器](../vsto/ribbon-designer.md)。  
  
#### 向功能区添加一个切换按钮  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
2.  在**“添加新项”**对话框中，选择**“功能区\(可视化设计器\)”**。  
  
3.  将新功能区更名为 **ManageTaskPaneRibbon**，然后单击“添加”。  
  
     **ManageTaskPaneRibbon.cs** 或 **ManageTaskPaneRibbon.vb** 文件将在功能区设计器中打开，并显示一个默认选项卡和组。  
  
4.  在功能区设计器中，单击“Group1”。  
  
5.  在“属性”窗口中，将“Label”属性设置为 **Task Pane Manager**。  
  
6.  从“工具箱”的“Office 功能区控件”选项卡中，将 **ToggleButton** 拖到“Task Pane Manager”组。  
  
7.  单击“toggleButton1”。  
  
8.  在“属性”窗口中，将“Label”属性设置为 **Show Task Pane**。  
  
## 设计自定义任务窗格的用户界面  
 没有针对自定义任务窗格的可视化设计器，但可以设计具有所需布局的用户控件。 稍后在本演练中，你将向自定义任务窗格添加用户控件。  
  
#### 若要设计自定义任务窗格的用户界面  
  
1.  在**“项目”**菜单上，单击**“添加用户控件”**。  
  
2.  在“添加新项”对话框中，将用户控件的名称更改为 **TaskPaneControl**，然后单击“添加”。  
  
     用户控件将在设计器中打开。  
  
3.  从“工具箱”的“公共控件”选项卡中，将 **TextBox** 控件拖到用户控件中。  
  
## 创建自定义任务窗格  
 若要在 VSTO 外接程序启动时创建自定义任务窗格，请将用户控件添加到 VSTO 外接程序的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序中的任务窗格中。 默认情况下，自定义任务窗格将不可见。 稍后在本演练中，你将添加可显示或隐藏任务窗格的代码，任务窗格在用户单击你添加到功能区的切换按钮时显示或隐藏。  
  
#### 若要创建自定义任务窗格  
  
1.  在**“解决方案资源管理器”**中，展开**“Excel”**。  
  
2.  右键单击 **ThisAddIn.cs** 或 **ThisAddIn.vb**，然后单击“查看代码”。  
  
3.  向 `ThisAddIn` 类添加下面的代码。 此代码将 `TaskPaneControl` 的实例声明为 `ThisAddIn` 的成员。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#1)]  
  
4.  将 `ThisAddIn_Startup` 事件处理程序替换为以下代码。 此代码向 `CustomTaskPanes` 字段添加 `TaskPaneControl` 对象，但它不显示自定义任务窗格（默认情况下，<xref:Microsoft.Office.Tools.CustomTaskPane> 类的 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> 属性是 **false**）。 Visual C\# 代码还会将一个事件处理程序附加到 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 事件。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#2)]  
  
5.  将以下方法添加到 `ThisAddIn` 类。 此方法处理 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 事件。 当用户通过单击**“关闭”**按钮 \(X\) 来关闭任务窗格时，此方法将更新功能区上切换按钮的状态。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#3)]  
  
6.  向 `ThisAddIn` 类添加以下属性。 此属性对其他类公开私有 `myCustomTaskPane1` 对象。 稍后在本演练中，你将向使用此属性的 `MyRibbon` 类添加代码。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#4)]  
  
## 通过使用切换按钮隐藏和显示自定义任务窗格  
 最后一步是添加可在用户单击功能区上的切换按钮时显示或隐藏自定义任务窗格的代码。  
  
#### 通过使用切换按钮显示和隐藏自定义任务窗格  
  
1.  在功能区设计器中，双击“显示任务窗格”切换按钮。  
  
     Visual Studio 会自动生成名为 `toggleButton1_Click` 的事件处理程序，它将处理切换按钮的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件。 Visual Studio 还会打开代码编辑器中的 **MyRibbon.cs** 或 **MyRibbon.vb** 文件。  
  
2.  将 `toggleButton1_Click` 事件处理程序替换为以下代码。 当用户单击切换按钮时，此代码显示或隐藏自定义任务窗格，具体取决于是按下还是未按下切换按钮。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ManageTaskPaneRibbon.cs#5)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ManageTaskPaneRibbon.vb#5)]  
  
## 测试外接程序  
 运行项目时，Excel 会打开，但不显示自定义任务窗格。 单击功能区上的切换按钮以测试代码。  
  
#### 测试 VSTO 外接程序  
  
1.  按 F5 运行项目。  
  
     确认 Excel 打开，且**“外接程序”**选项卡显示在功能区中。  
  
2.  单击功能区上的**“外接程序”**选项卡。  
  
3.  在**“任务窗格管理器”**组中，单击**“显示任务窗格”**切换按钮。  
  
     验证当点击切换按钮时，任务窗格交替显示和隐藏。  
  
4.  当任务窗格可见时，单击任务窗格一角的**“关闭”**按钮 \(X\)。  
  
     验证切换按钮显示为未按下。  
  
## 后续步骤  
 可从以下主题了解有关如何创建自定义任务窗格的详细信息：  
  
-   在 VSTO 外接程序中为不同应用程序创建自定义任务窗格。 有关支持自定义任务窗格的应用程序的详细信息，请参阅 [自定义任务窗格](../vsto/custom-task-panes.md)。  
  
-   从自定义任务窗格自动化应用程序。 有关详细信息，请参阅[演练：从自定义任务窗格自动化应用程序](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)。  
  
-   为 Outlook 中打开的每封电子邮件创建自定义任务窗格。 有关详细信息，请参阅[演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
## 请参阅  
 [自定义任务窗格](../vsto/custom-task-panes.md)   
 [如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [演练：从自定义任务窗格自动化应用程序](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [功能区概述](../vsto/ribbon-overview.md)  
  
  