---
title: "演练： 创建带有关联和启动窗体的工作流 |Microsoft 文档"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa95c519ab24ba042b6a1adfa71c64499b18d4c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>演练：创建带有关联窗体和启动窗体的工作流
  本演练演示如何创建包含关联和启动窗体使用的基本顺序工作流。 这些是启用参数时首次将其关联的 SharePoint 管理员 （关联形式），并由用户 （启动窗体） 启动工作流时要添加到工作流的 ASPX 窗体。  
  
 本演练中概述了用户要创建用于费用报告的审批工作，这些流具有以下要求的方案：  
  
-   在工作流与列表关联时，管理员系统会提示他们美元限制输入支出报表的其中一个关联窗体。  
  
-   员工将其支出报表上载到共享文档列表，启动工作流，然后输入工作流启动窗体中总费用。  
  
-   如果员工支出报表总超过管理员的预定义的限制，是为员工的经理批准的费用报表创建任务。 不过，如果员工的支出报表总小于或等于支出限制，则自动批准的消息都写入到工作流的历史记录列表。  
  
 本演练阐释了以下任务：  
  
-   创建 SharePoint 列表定义顺序工作流项目中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   创建工作流的计划。  
  
-   处理工作流活动事件。  
  
-   创建工作流关联和启动窗体。  
  
-   将工作流相关联。  
  
-   手动启动工作流。  
  
> [!NOTE]  
>  尽管本演练中使用的顺序工作流项目，该过程是相同的状态机工作流。  
>   
>  此外，可能会出现你的计算机的不同名称或位置用于某些[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]以下说明中的用户界面元素。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]你具有的版本和你使用的设置确定这些元素。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>创建 SharePoint 顺序工作流项目  
 首先，创建中的顺序工作流项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 顺序工作流是一系列按顺序执行的最后一个活动完成之前的步骤。 在此过程中，你将创建适用于 SharePoint 中的共享文档列表的顺序工作流。 工作流向导可将工作流的站点或列表定义与相关联，并使你能够确定工作流何时开始。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要创建 SharePoint 顺序工作流项目  
  
1.  在菜单栏上，选择**文件**，**新建**，**项目**以显示**新项目**对话框。  
  
2.  展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**节点。  
  
3.  在**模板**窗格中，选择**SharePoint 2010 项目**项目模板。  
  
4.  在**名称**框中，输入**ExpenseReport** ，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
5.  在**指定用于调试的站点和安全性级别**页上，选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮以接受信任级别和默认站点。  
  
     此步骤还将解决方案的信任级别设置为场解决方案，这是工作流项目的唯一可用的选项。  
  
6.  在 **“解决方案资源管理器”**中，选择项目节点。  
  
7.  在菜单栏上，选择**项目**，**添加新项**。  
  
8.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**节点。  
  
9. 在**模板**窗格中，选择**顺序工作流 （仅场解决方案）**模板，然后选择**添加**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
10. 在**指定用于调试的工作流名称**页上，接受默认名称 (**ExpenseReport-Workflow1**)。 保留默认工作流模板类型值 (**列表工作流)**。 选择**下一步**按钮。  
  
11. 在**想让 Visual Studio 以自动将工作流关联的调试会话中？**页上，清除自动将你的工作流模板相关联如果签入的框。  
  
     此步骤能让您手动将带有共享文档列表更高版本上，其中显示了工作关联窗体的工作流相关联。  
  
12. 选择**完成**按钮。  
  
## <a name="adding-an-association-form-to-the-workflow"></a>添加到工作流关联窗体  
 接下来，创建。ASPX SharePoint 管理员首先工作流将与相关联的支出报表文档时，将显示的关联窗体。  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>若要添加到工作流关联窗体  
  
1.  选择**Workflow1**中的节点**解决方案资源管理器**。  
  
2.  在菜单栏上，选择**项目**，**添加新项**以显示**添加新项**对话框。  
  
3.  在对话框框中的树视图中，展开**Visual C#**或**Visual Basic** （具体取决于你项目的语言），展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在模板列表中，选择**工作流关联窗体**模板。  
  
5.  在**名称**文本框中，输入**ExpenseReportAssocForm.aspx**。  
  
6.  选择**添加**按钮以向项目添加窗体。  
  
## <a name="designing-and-coding-the-association-form"></a>设计和编码关联窗体  
 在此过程中，你通过向其添加控件和代码引入在关联窗体的功能。  
  
#### <a name="to-design-and-code-the-association-form"></a>若要设计和关联窗体的代码  
  
1.  在关联窗体 (ExpenseReportAssocForm.aspx) 找到`asp:Content`元素具有`ID="Main"`。  
  
2.  此内容的元素中的第一行，后面直接添加以下代码以创建标签和提示输入的费用审批限额的文本框中 (*AutoApproveLimit*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  展开**ExpenseReportAssocForm.aspx**文件中**解决方案资源管理器**以显示及其依赖文件。  
  
    > [!NOTE]  
    >  如果你的项目在[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]，必须选择**查看所有文件**按钮以执行此步骤。  
  
4.  打开 ExpenseReportAssocForm.aspx 文件的快捷菜单，然后选择**查看代码**。  
  
5.  替换`GetAssociationData`方法：  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>将启动窗体添加到工作流  
 接下来，创建将显示当用户针对其支出报表运行工作流启动窗体。  
  
#### <a name="to-create-an-initiation-form"></a>若要创建的启动窗体  
  
1.  选择**Workflow1**中的节点**解决方案资源管理器**。  
  
2.  在菜单栏上，选择**项目**，**添加新项**显示**添加新项**对话框。  
  
3.  在对话框框中的树视图中，展开**Visual C#**或**Visual Basic** （具体取决于你项目的语言），展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在模板列表中，选择**工作流启动窗体**模板。  
  
5.  在**名称**文本框中，输入**ExpenseReportInitForm.aspx**。  
  
6.  选择**添加**按钮以向项目添加窗体。  
  
## <a name="designing-and-coding-the-initiation-form"></a>设计和编码启动窗体  
 接下来，通过向其添加控件和代码中引入在启动窗体的功能。  
  
#### <a name="to-code-the-initiation-form"></a>若要启动窗体的代码  
  
1.  在启动窗体 (ExpenseReportInitForm.aspx) 找到`asp:Content`包含的元素`ID="Main"`。  
  
2.  紧接在此内容的元素中第一行后面添加以下代码以创建标签和显示的费用审批限额的文本框中 (*AutoApproveLimit*)，输入在关联窗体中和另一个标签和文本框中输入费用总额提示 (*ExpenseTotal*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  展开**ExpenseReportInitForm.aspx**文件中**解决方案资源管理器**以显示及其依赖文件。  
  
4.  打开 ExpenseReportInitForm.aspx 文件的快捷菜单，然后选择**查看代码**。  
  
5.  替换`Page_Load`方法使用下面的示例：  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  替换`GetInitiationData`方法使用下面的示例：  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="customizing-the-workflow"></a>自定义工作流  
 接下来，自定义工作流。 更高版本，会将关联到工作流的两种形式。  
  
#### <a name="to-customize-the-workflow"></a>若要自定义工作流  
  
1.  通过在项目中打开 Workflow1 在工作流设计器中显示工作流。  
  
2.  在**工具箱**，展开**Windows Workflow v3.0**节点并找到**IfElse**活动。  
  
3.  将此活动添加到工作流中，通过执行以下步骤之一：  
  
    -   打开的快捷菜单**IfElse**活动，选择**复制**，打开的行的快捷菜单**onWorkflowActivated1**中工作流设计器中，活动然后选择**粘贴**。  
  
    -   拖动**IfElse**活动从**工具箱**，并将其连接到下一行**onWorkflowActiviated1**工作流设计器中的活动。  
  
4.  在工具箱中，展开**SharePoint 工作流**节点并找到**CreateTask**活动。  
  
5.  将此活动添加到工作流中，通过执行以下步骤之一：  
  
    -   打开的快捷菜单**CreateTask**活动，选择**复制**，打开两种状态之一的快捷菜单**在此处放置活动**领域提供**IfElseActivity1**中工作流设计器中，然后选择**粘贴**。  
  
    -   拖动**CreateTask**活动从**工具箱**到两种状态之一**在此处放置活动**领域提供**IfElseActivity1**。  
  
6.  在**属性**窗口中，输入属性值*taskToken*为**CorrelationToken**属性。  
  
7.  展开**CorrelationToken**属性通过选择加号 (![TreeView 加号](../sharepoint/media/plus.gif "TreeView 加号")) 它的旁边。  
  
8.  在选择的下拉箭头**OwnerActivityName**子属性，并设置*Workflow1*值。  
  
9. 选择**TaskId**属性，然后选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")) 按钮以显示**绑定属性**对话框。  
  
10. 选择**绑定到新成员**选项卡上，选择**创建字段**选项按钮，，然后选择**确定**按钮。  
  
11. 选择**TaskProperties**属性，然后选择省略号 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")) 按钮以显示**将属性绑定**对话框。  
  
12. 选择**绑定到新成员**选项卡上，选择**创建字段**选项按钮，，然后选择**确定**按钮。  
  
13. 在**工具箱**，展开**SharePoint 工作流**节点，并找到**LogToHistoryListActivity**活动。  
  
14. 将此活动添加到工作流中，通过执行以下步骤之一：  
  
    -   打开的快捷菜单**LogToHistoryListActivity**活动，选择**复制**，其他打开的快捷菜单**在此处放置活动**内区域**IfElseActivity1**中工作流设计器中，然后选择**粘贴**。  
  
    -   拖动**LogToHistoryListActivity**活动从**工具箱**，并将其放到另**在此处放置活动**内的区域**IfElseActivity1**.  
  
## <a name="adding-code-to-the-workflow"></a>将代码添加到工作流  
 接下来，将代码添加到要为其提供功能的工作流。  
  
#### <a name="to-add-code-to-the-workflow"></a>若要将代码添加到工作流  
  
1.  打开的快捷菜单**createTask1**活动在工作流设计器中，然后选择**查看代码**。  
  
2.  添加以下方法：  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  在代码中，替换`somedomain\\someuser`使用域和用户的名称，为其将创建任务，例如，"`Office\\JoeSch`"。 用于测试很容易使用开发时所用的帐户。  
  
3.  下面`MethodInvoking`方法，添加下面的示例：  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  在工作流设计器中，选择**ifElseBranchActivity1**活动。  
  
5.  在**属性**窗口中，选择的下拉箭头**条件**属性，且然后将其设置*代码条件*值。  
  
6.  展开**条件**属性通过选择加号 (![TreeView 加号](../sharepoint/media/plus.gif "TreeView 加号")) 旁边，然后将其值设置为*checkApprovalNeeded*.  
  
7.  在工作流设计器中，打开快捷菜单**logToHistoryListActivity1**活动，然后选择**生成处理程序**生成的空方法`MethodInvoking`事件。  
  
8.  替换`MethodInvoking`替换为以下代码：  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. 选择 F5 键调试程序。  
  
     这可以编译应用程序，将其打包、 将其部署、 激活其功能，回收[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]应用程序池，并在指定位置的浏览器然后开始**站点 Url**属性。  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>将工作流保存到文档列表相关联  
 接下来，通过将相关联的工作流中显示工作流关联窗体**SharedDocuments** SharePoint 站点上的列表。  
  
#### <a name="to-associate-the-workflow"></a>若要将工作流关联  
  
1.  选择**共享文档**快速启动栏上的链接。  
  
2.  选择**库**链接**库工具**选项卡，然后选择**库设置**功能区按钮。  
  
3.  在**权限和管理**部分中，选择**工作流设置**链接，然后选择**添加工作流**链接**工作流**页。  
  
4.  在工作流设置页中的顶层列表中，选择**ExpenseReport-Workflow1**模板。  
  
5.  在下一步的字段中，输入**ExpenseReportWorkflow** ，然后选择**下一步**按钮。  
  
     这将与流相关联**共享文档**列表并显示工作流关联窗体。  
  
6.  在**自动批准限制**文本框中，输入**1200年**，然后选择**将关联的工作流**按钮。  
  
## <a name="starting-the-workflow"></a>启动工作流  
 接下来，将工作流保存到中的文档之一相关联**共享文档**列表以显示工作流启动窗体。  
  
#### <a name="to-start-the-workflow"></a>若要启动工作流  
  
1.  在 SharePoint 页上，选择**主页**按钮。  
  
2.  选择**共享文档**上快速启动栏上显示的链接**共享文档**列表。  
  
3.  选择**文档**链接**库工具**页上，顶部选项卡，然后选择**上载文档**要上载到新文档的功能区上的按钮**共享文档**列表。  
  
4.  在**上载文档**对话框框中，选择**浏览**按钮，选择任何文档文件，选择**打开**按钮，，然后选择**确定**按钮。  
  
     可以更改此对话框中中的文档的设置，但将其保留为默认值，通过选择**保存**按钮。  
  
5.  选择已上载的文档中，选择的下拉箭头，显示，然后选择**工作流**项。  
  
6.  选择 ExpenseReportWorkflow 旁边的映像。  
  
     此时将显示工作流启动窗体。 (请注意的值显示在**自动批准限制**框是只读的因为它已在关联窗体中输入。)  
  
7.  在**支出总**文本框中，输入**1600年**，然后选择**启动工作流**按钮。  
  
     此时将显示**共享文档**再次列表。 一个名为的新列**ExpenseReportWorkflow**值**已完成**添加到工作流只是启动的项。  
  
8.  选择已上载的文档旁边的下拉箭头，然后选择**工作流**项目以显示工作流状态页。 选择**已完成**值下**完成工作流**。 下面列出任务**任务**部分。  
  
9. 请选择要显示其任务详细信息的任务的标题。  
  
10. 返回到**SharedDocuments**列表并重新启动使用同一文档或一个不同的工作流。  
  
11. 小于或等于关联页上输入的金额的启动页面上输入金额 (**1200年**)。  
  
     当发生这种情况时，而不是任务创建历史记录列表中的条目。 该项显示在**工作流历史记录**工作流状态页部分。 请记下的消息中**结果**的历史记录事件的列。 它包含输入中的文本`logToHistoryListActivity1.MethodInvoking`包括这是自动批准的事件。  
  
## <a name="next-steps"></a>后续步骤  
 你可以了解有关如何从下面这些主题中创建工作流模板的详细信息：  
  
-   若要了解有关 SharePoint 工作流的详细信息，请参阅[Windows SharePoint Services 中的工作流](http://go.microsoft.com/fwlink/?LinkID=166275)。  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [演练：将应用程序页添加到工作流](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  