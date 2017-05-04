---
title: "演练：创建带有关联窗体和启动窗体的工作流 | Microsoft Docs"
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
  - "关联窗体 [Visual Studio 中的 SharePoint 开发]"
  - "启动窗体 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 工作流关联窗体"
  - "Visual Studio 中的 SharePoint 开发, 工作流启动窗体"
  - "Visual Studio 中的 SharePoint 开发, 工作流"
  - "工作流 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 演练：创建带有关联窗体和启动窗体的工作流
  本演练演示如何创建结合使用关联窗体和启动窗体的基本顺序工作流。  关联窗体和启动窗体都是 ASPX 窗体，在 SharePoint 管理员首次关联工作流（关联窗体）时以及在用户启动工作流（启动窗体）时，可利用这些窗体将参数添加到工作流中。  
  
 本演练概述了一个应用场景，即用户希望为零用金报销单创建一个具有下列要求的审批工作流：  
  
-   当工作流与一个列表关联时，将为管理员显示一个关联窗体以让其输入零用金报销单的金额限制。  
  
-   雇员将零用金报销单上载到“共享文档”列表，启动工作流，然后在工作流启动窗体中输入费用总额。  
  
-   如果某个雇员的零用金报销单的费用总额超出了管理员预定义的限额，则为雇员的经理创建一个任务来审批零用金报销单。  但是，如果雇员的零用金报销单的费用总额小于或等于费用限额，则将自动批准的消息写入到工作流的历史记录列表中。  
  
 本演练阐释了以下任务：  
  
-   在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建 SharePoint 列表定义顺序工作流项目。  
  
-   创建工作流时间表。  
  
-   处理工作流活动事件。  
  
-   创建工作流关联窗体和工作流启动窗体。  
  
-   关联工作流。  
  
-   手动启动工作流。  
  
> [!NOTE]  
>  虽然本演练使用的是顺序工作流项目，但过程与状态机工作流的过程相同。  
>   
>  此外，以下说明中的某些 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 用户界面元素与在您的计算机上显示的名称或位置不同。  您安装的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 版本以及使用的设置决定了这些元素。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 创建 SharePoint 顺序工作流项目  
 首先，在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建一个顺序工作流项目。  顺序工作流是一系列步骤，这些步骤按顺序执行，直到最后一项活动完成。  在此过程中，您将创建一个应用于 SharePoint 中的“共享文档”列表的顺序工作流。  利用此工作流的向导，您可以将此工作流与网站或列表定义关联，并可以确定工作流的启动时间。  
  
#### 创建 SharePoint 顺序工作流项目  
  
1.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**，以显示**“新建项目”**对话框。  
  
2.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
3.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 项目模板。  
  
4.  在**“名称”**框中，输入ExpenseReport ，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
5.  在 **指定用于调试的网站和安全级别** 页中，选择 **部署为场解决方案** 选项按钮，然后选择 **完成** 按钮以接受默认站点和信任级别。  
  
     此步骤还会将解决方案的信任级别设置为场解决方案（工作流项目的唯一可用选项）。  
  
6.  在**“解决方案资源管理器”**中，选择项目节点。  
  
7.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
8.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
9. 在 **模板** 窗格中，选择 **顺序工作流 \(仅场解决方案\)** 模板，然后选择 **添加** 按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
10. 在**“指定用于调试的工作流名称”**页上，接受默认名称（**“ExpenseReport \- Workflow1”**）。  保留默认工作流模板类型值（**“列表工作流”**）。  选择**“下一步”**按钮。  
  
11. 在**“是否希望 Visual Studio 在调试会话中自动关联工作流?”**页中，清除用于自动关联工作流模板的框（如果该框处于选中状态）。  
  
     利用此步骤，您可以稍后手动将工作流与显示关联窗体的“共享文档”列表关联。  
  
12. 选择**“完成”**按钮。  
  
## 将关联窗体添加到工作流  
 接下来，创建一个 .ASPX 关联窗体，当 SharePoint 管理员首次将工作流与零用金报销单文档相关联时，将显示此窗体。  
  
#### 将关联窗体添加到工作流  
  
1.  在 **“解决方案资源管理器”**中，选择**Workflow1**节点。  
  
2.  在菜单栏上选择**“项目”“添加新项”**以显示**“添加新项”**对话框。  
  
3.  在该对话框树视图中，展开**“Visual C\#”**或**“Visual Basic”**（取决于项目语言），再展开**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在模板列表中，选择 **工作流关联窗体** 模板。  
  
5.  在**“名称”**文本框中，键入 ExpenseReportAssocForm.aspx。  
  
6.  选择**“添加”**按钮，将该窗体添加到项目中。  
  
## 设计关联窗体并对其进行编码  
 在此过程中，通过在关联窗体中添加控件和代码来引入功能。  
  
#### 设计关联窗体并对其进行编码  
  
1.  在关联窗体 \(ExpenseReportAssocForm.aspx\) 中，找到具有 `ID="Main"` 的 `asp:Content` 元素。  
  
2.  紧接在此内容元素中的第一行后面添加以下代码，以创建一个用于提示输入费用审批限额 \(*AutoApproveLimit*\) 的标签和文本框：  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  展开**“解决方案资源管理器”**中的**“ExpenseReportAssocForm.aspx”**文件以显示其从属文件。  
  
    > [!NOTE]  
    >  如果项目位于 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 中，您必须选择**“查看所有文件”**按钮才能执行此步骤。  
  
4.  打开 ExpenseReportAssocForm.aspx 文件的快捷菜单，选择 **查看代码**。  
  
5.  将 `GetAssociationData` 方法替换为：  
  
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
  
## 将启动窗体添加到工作流  
 接下来，创建在用户针对其零用金报销单运行工作流时显示的启动窗体。  
  
#### 创建启动窗体  
  
1.  在 **“解决方案资源管理器”**中，选择**Workflow1**节点。  
  
2.  在菜单栏上，选择**“项目”**，**“添加新项”**以显示**“添加新项”**对话框。  
  
3.  在该对话框树视图中，展开**“Visual C\#”**或**“Visual Basic”** （取决于项目语言），再展开**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在模板列表中，选择 **工作流初始窗体** 模板。  
  
5.  在**“名称”**文本框中，键入 ExpenseReportInitForm.aspx。  
  
6.  选择**“添加”**按钮，将该窗体添加到项目中。  
  
## 设计启动窗体并对其进行编码  
 接下来，通过在启动窗体中添加控件和代码来引入功能。  
  
#### 对启动窗体进行编码  
  
1.  在启动窗体 \(ExpenseReportInitForm.aspx\) 中，找到具有 `ID="Main"` 的 `asp:Content` 元素。  
  
2.  紧接在此内容元素中的第一行后面添加以下代码，以创建一个显示已在关联窗体中输入的费用审批限额 \(*AutoApproveLimit*\) 的标签和文本框，以及另一个提示输入费用总额 \(*ExpenseTotal*\) 的标签和文本框：  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  展开**“解决方案资源管理器”**中的**“ExpenseReportInitForm.aspx”**文件以显示其从属文件。  
  
4.  打开 ExpenseReportInitForm.aspx 文件的快捷菜单，选择 **查看代码**。  
  
5.  将 `Page_Load` 方法替换为以下示例：  
  
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
  
6.  将 `GetInitiationData` 方法替换为以下示例：  
  
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
  
## 自定义工作流  
 接下来，自定义工作流。  然后，将两个窗体关联到工作流。  
  
#### 自定义工作流  
  
1.  通过打开项目中的 Workflow1，在工作流设计器中显示工作流。  
  
2.  在**工具箱**中，展开**Windows Workflow v3.0**节点，并找到**IfElse**活动。  
  
3.  通过执行以下任一步骤，将此活动添加到工作流：  
  
    -   打开**IfElse**活动的快捷菜单，选择“复制”，然后打开工作流设计器中的**onWorkflowActivated1**活动下行的快捷菜单，然后选择“粘贴”。  
  
    -   在工作流设计器中，从**工具箱**拖拽**IfElse**活动，并将该活动与**onWorkflowActiviated1**活动下的行连接。  
  
4.  在工具箱中，展开**“SharePoint 工作流”**节点并找到**“CreateTask”**活动。  
  
5.  通过执行以下任一步骤，将此活动添加到工作流：  
  
    -   打开 **CreateTask** 活动的快捷菜单，选择 **复制**，在工作流设计器，打开 IfElseActivity1 中的两个 **将 Activity 拖放至此** 区域之一的快捷菜单，然后选择 **粘贴**。  
  
    -   将 **工具箱** 的 **CreateTask** 活动拖到 IfElseActivity1 中的两个 **将 Activity 拖放至此** 区域之一上面。  
  
6.  在**“属性”**窗口中，为 **CorrelationToken** 属性输入属性值 *taskToken*。  
  
7.  通过选择 **CorrelationToken** 属性旁边的加号 \(![TreeView 加号](../sharepoint/media/plus.png "TreeView 加号")\) 来展开此属性。  
  
8.  选择 **OwnerActivityName** 子属性上的下拉箭头，然后设置 *Workflow1* 值。  
  
9. 选择 **TaskId** 属性，然后选择省略号 \(![ASP.NET 移动设计器中的省略号](../sharepoint/media/mwellipsis.png "ASP.NET 移动设计器中的省略号")\) 按钮以显示**“绑定属性”**对话框。  
  
10. 选择 **绑定到新成员** 选项卡，选择 **创建字段** 选项按钮，然后选择 **确定** 按钮。  
  
11. 选择 **TaskProperties** 属性，然后选择省略号 \(![ASP.NET 移动设计器中的省略号](../sharepoint/media/mwellipsis.png "ASP.NET 移动设计器中的省略号")\) 按钮以显示**“绑定属性”**对话框。  
  
12. 选择 **绑定到新成员** 选项卡，选择 **创建字段** 选项按钮，然后选择 **确定** 按钮。  
  
13. 在**工具箱**中，展开**SharePoint 工作流**节点,并找到**LogToHistoryListActivity**活动。  
  
14. 通过执行以下任一步骤，将此活动添加到工作流：  
  
    -   打开 **LogToHistoryListActivity** 活动的快捷菜单，选择 **复制**，在工作流设计器，打开 IfElseActivity1 中的两个 **将 Activity 拖放至此** 区域之一的快捷菜单，然后选择 **粘贴**。  
  
    -   将 **工具箱**的 **LogToHistoryListActivity** 活动，拖到其他区域 **将 Activity 拖放至此** IfElseActivity1 中。  
  
## 在工作流中添加代码  
 接下来，在工作流中添加代码以引入功能。  
  
#### 在工作流中添加代码  
  
1.  在工作流设计器，打开 **createTask1** 活动的快捷菜单，然后选择 **查看代码**。  
  
2.  添加下面的方法：  
  
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
    >  在代码中，将 `somedomain\\someuser` 替换为将为其创建任务的域和用户名，如“`Office\\JoeSch`”。  使用开发时所用的帐户进行测试最为轻松。  
  
3.  在 `MethodInvoking` 方法下添加以下示例：  
  
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
  
4.  在工作流设计器中，选择**“ifElseBranchActivity1”**活动。  
  
5.  在**“属性”**窗口中，选择**“Condition”**属性的下拉箭头，然后设置 *Code Condition*的值。  
  
6.  通过选择**“Condition”**属性旁边的加号 \(![TreeView 加号](../sharepoint/media/plus.png "TreeView 加号")\) 来展开此属性，然后将其值设置为 *checkApprovalNeeded*。  
  
7.  在工作流设计器中，打开**“logToHistoryListActivity1”**活动的快捷菜单，然后选择**“生成处理程序”**，以便为 `MethodInvoking` 事件生成空方法。  
  
8.  将 `MethodInvoking` 代码替换为下面的内容：  
  
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
  
9. 选择键 F5 调试程序。  
  
     这将编译应用程序，对其进行打包和部署，激活其功能，回收 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 应用程序池，然后启动位于**“Site Url”**属性中指定的位置的浏览器。  
  
## 将工作流关联到文档列表  
 接下来，通过将工作流与 SharePoint 网站上的**“共享文档”**列表相关联来显示工作流关联窗体。  
  
#### 关联工作流  
  
1.  选择快速启动栏上的**“共享文档”**链接。  
  
2.  在**库工具**选项卡上，选择**库**链接，然后选择**“库设置”**功能区按钮。  
  
3.  在**“权限和管理”**部分中，选择**“工作流设置”**链接，然后选择**“工作流”**页上的**“添加工作流”**链接。  
  
4.  在工作流设置页的顶部列表中，选择**“ExpenseReport \- Workflow1”**模板。  
  
5.  在下一个字段中，键入 ExpenseReportWorkflow，然后选择**“下一步”**按钮。  
  
     这会将工作流与**“共享文档”**列表相关联并显示工作流关联窗体。  
  
6.  在**“Auto Approval Limit”（自动审批限额）**文本框中，键入 1200，然后选择**“关联工作流”**按钮。  
  
## 启动工作流  
 然后将工作流关联到**“共享文档”**列表中的某个文档以显示工作流启动窗体。  
  
#### 启动工作流  
  
1.  在 SharePoint 页上，选择**“主页”**按钮。  
  
2.  在快速启动栏上，选择 **共享文档** 链接，显示 **共享文档** 列表。  
  
3.  选择页顶部的**“库工具”**选项卡上的**“文档”**链接，然后选择功能区上的**“上载文档”**按钮，将新文档上载到**“共享文档”**列表中。  
  
4.  在 **上载文档** 对话框中，选择 **浏览** 按钮，选择任何文档文件，选择 **打开** 按钮，然后选择 **确定** 按钮。  
  
     虽然您可以在对话框更改文档的设置，但此时请选择**“保存”**按钮，以保留这些文档设置的默认值。  
  
5.  选择已上载文档，选择出现的下拉箭头，然后选择 **工作流** 项。  
  
6.  选择 ExpenseReportWorkflow 旁边的图像。  
  
     这将显示工作流启动窗体。（请注意，**“Auto Approval Limit”（自动审批限额）**框中显示的值是只读的，因为此值是先前在关联窗体中输入的。）  
  
7.  在 **零用金总计** 文本框中，键入 1600，然后选择 **启动工作流** 按钮。  
  
     这将再次显示**“共享文档”**列表。  将带有**“Completed”**值的名为**“ExpenseReportWorkflow”**的新列添加到工作流刚启动的项中。  
  
8.  选择已上载文档旁边的下拉箭头，然后选择**“工作流”**项以显示工作流状态页。  选择**“已完成工作流”**下的**“已完成”**的值。  这将在**“任务”**部分下方列出任务。  
  
9. 选择任务的标题以显示其任务的详细信息。  
  
10. 返回到**“共享文档”**列表并使用同一文档或其他文档重新启动工作流。  
  
11. 在启动页上输入一个小于或等于关联页上输入的金额 \(1200\)。  
  
     在执行此操作时，会在历史记录列表中创建一个项而不是任务。  该项显示在工作流状态页的**“工作流历史记录”**部分中。  请注意历史记录事件的**“结果”**列中的消息。  它包含 `logToHistoryListActivity1.MethodInvoking` 事件中输入的文本，该文本包括已自动审批的金额。  
  
## 后续步骤  
 可从以下主题中了解有关如何创建工作流模板的更多信息：  
  
-   若要了解有关 SharePoint 工作流，请参见 [在 Windows SharePoint Services 中的工作流](http://go.microsoft.com/fwlink/?LinkID=166275)。  
  
## 请参阅  
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [演练：向工作流中添加应用程序页](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  