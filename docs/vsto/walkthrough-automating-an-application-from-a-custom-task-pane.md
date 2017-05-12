---
title: "演练：从自定义任务窗格自动化应用程序"
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
  - "任务窗格 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "PowerPoint [Visual Studio 中的 Office 开发]，自定义任务窗格"
  - "自动化 Office 应用程序"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]，自动化应用程序"
  - "自定义任务窗格 [Visual Studio 中的 Office 开发]，PowerPoint"
  - "任务窗格 [Visual Studio 中的 Office 开发]，自动化应用程序"
ms.assetid: 77be5ab5-e330-4564-87ec-9cba564ba8f9
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 演练：从自定义任务窗格自动化应用程序
  本演练演示了如何创建实现 PowerPoint 自动化的自定义任务窗格。 当用户单击自定义任务窗格中的 <xref:System.Windows.Forms.MonthCalendar> 控件时，自定义任务窗格向一张幻灯片中插入日期。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 虽然本演练具体使用的是 PowerPoint，但其中所阐释的概念同样适用于上面所列的应用程序。  
  
 本演练阐释了以下任务：  
  
-   设计自定义任务窗格的用户界面。  
  
-   从自定义任务窗格中实现 PowerPoint 自动化。  
  
-   在 PowerPoint 中显示自定义任务窗格。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 或 [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)]。  
  
## 创建外接程序项目  
 第一步是创建 PowerPoint 的 VSTO 外接程序项目。  
  
#### 创建新项目  
  
1.  使用 PowerPoint 外接程序项目模板创建名为 **MyAddIn** 的 PowerPoint VSTO 外接程序项目。 有关更多信息，请参见[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将打开 **ThisAddIn.cs** 或 **ThisAddIn.vb** 代码文件并将 **MyAddIn** 项目添加到**解决方案资源管理器**中。  
  
## 设计自定义任务窗格的用户界面  
 没有针对自定义任务窗格的可视化设计器，但可以设计具有所需布局的用户控件。 稍后在本演练中，你将向自定义任务窗格添加用户控件。  
  
#### 若要设计自定义任务窗格的用户界面  
  
1.  在**“项目”**菜单上，单击**“添加用户控件”**。  
  
2.  在“添加新项”对话框中，将用户控件的名称更改为 **MyUserControl**，然后单击“添加”。  
  
     用户控件将在设计器中打开。  
  
3.  从“工具箱”的“公共控件”选项卡中，将 **MonthCalendar** 控件拖到用户控件中。  
  
     如果 **MonthCalendar** 控件大于用户控件的设计图面，则调整用户控件的大小以适合 **MonthCalendar** 控件。  
  
## 从自定义任务窗格中实现 PowerPoint 自动化  
 VSTO 外接程序的作用是在活动演示文稿的第一张幻灯片中放置所选日期。 使用控件的 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 事件以在发生更改时添加所选日期。  
  
#### 若要从自定义任务窗格中实现 PowerPoint 自动化  
  
1.  在设计器中，双击 <xref:System.Windows.Forms.MonthCalendar> 控件。  
  
     此时会打开 **MyUserControl.cs** 或 **MyUserControl.vb** 文件，并创建 <xref:System.Windows.Forms.MonthCalendar.DateChanged> 事件的事件处理程序。  
  
2.  将下面的代码添加到文件的顶部。 此代码将为 <xref:Microsoft.Office.Core> 和 <xref:Microsoft.Office.Interop.PowerPoint> 命名空间创建别名。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#1)]  
  
3.  向 `MyUserControl` 类添加下面的代码。 此代码将 <xref:Microsoft.Office.Interop.PowerPoint.Shape> 对象声明为 `MyUserControl` 的成员。 在下面的步骤中，将使用此 <xref:Microsoft.Office.Interop.PowerPoint.Shape> 在活动演示文稿的幻灯片中添加文本框。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#2)]  
  
4.  将 `monthCalendar1_DateChanged` 事件处理程序替换为以下代码。 此代码向活动演示文稿的第一张幻灯片中添加文本框，然后向文本框中添加当前选定的日期。 此代码将使用 `Globals.ThisAddIn` 对象来访问 PowerPoint 的对象模型。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#3)]  
  
5.  在**解决方案资源管理器**中，右键单击 **MyAddIn** 项目，然后单击“生成”。 验证此项目是否已生成且未发生错误。  
  
## 显示自定义任务窗格  
 若要在 VSTO 外接程序启动时显示自定义任务窗格，请将用户控件添加到 VSTO 外接程序的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件处理程序中的任务窗格中。  
  
#### 若要显示自定义任务窗格  
  
1.  在**解决方案资源管理器**中，展开 **PowerPoint**。  
  
2.  右键单击 **ThisAddIn.cs** 或 **ThisAddIn.vb**，然后单击“查看代码”。  
  
3.  向 `ThisAddIn` 类添加下面的代码。 此代码将 `MyUserControl` 和 <xref:Microsoft.Office.Tools.CustomTaskPane> 的实例声明为 `ThisAddIn` 类的成员。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#4)]  
  
4.  将 `ThisAddIn_Startup` 事件处理程序替换为以下代码。 此代码通过将 `MyUserControl` 对象添加到 `CustomTaskPanes` 集合来创建新 <xref:Microsoft.Office.Tools.CustomTaskPane>。 代码还将显示任务窗格。  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#5)]  
  
## 测试外接程序  
 运行该项目时，会打开 PowerPoint，VSTO 外接程序将显示自定义任务窗格。 单击 <xref:System.Windows.Forms.MonthCalendar> 控件以测试代码。  
  
#### 测试 VSTO 外接程序  
  
1.  按 F5 运行项目。  
  
2.  确认自定义任务窗格是可见的。  
  
3.  单击任务窗格上 <xref:System.Windows.Forms.MonthCalendar> 控件中的某个日期。  
  
     将向活动演示文稿的第一张幻灯片中添加日期。  
  
## 后续步骤  
 可从以下主题了解有关如何创建自定义任务窗格的详细信息：  
  
-   在 VSTO 外接程序中为不同应用程序创建自定义任务窗格。 有关支持自定义任务窗格的应用程序的详细信息，请参阅 [自定义任务窗格](../vsto/custom-task-panes.md)。  
  
-   创建一个用于隐藏或显示自定义任务窗格的功能区按钮。 有关更多信息，请参见[演练：将自定义任务窗格与功能区按钮同步](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)。  
  
-   为 Outlook 中打开的每封电子邮件创建自定义任务窗格。 有关更多信息，请参见[演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
## 请参阅  
 [自定义任务窗格](../vsto/custom-task-panes.md)   
 [如何：向应用程序中添加自定义任务窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [演练：将自定义任务窗格与功能区按钮同步](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [演练：为 Outlook 中的电子邮件显示自定义任务窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  