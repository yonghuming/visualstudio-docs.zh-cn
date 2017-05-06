---
title: "演练：创建和调试 SharePoint 工作流解决方案"
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
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 工作流"
  - "工作流 [Visual Studio 中的 SharePoint 开发]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 演练：创建和调试 SharePoint 工作流解决方案
  此演练演示如何创建基本的顺序工作流模板。  工作流检查共享文档库的属性，以确定文档是否已评审。  如果文档已评审，则工作流完成。  
  
 本演练阐释了以下任务：  
  
-   在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建 SharePoint 列表定义顺序工作流项目。  
  
-   创建工作流活动。  
  
-   处理工作流活动事件。  
  
> [!NOTE]  
>  虽然本演练使用的是顺序工作流项目，但过程与状态机工作流项目的过程相同。  
>   
>  另外，以下说明中的某些 Visual Studio 用户界面元素在您的计算机上出现的名称或位置可能会不同。  你安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## 向 SharePoint 共享文档库中添加属性  
 为跟踪**“共享文档”**库中文档的评审状态，我们将为 SharePoint 网站上的共享文档创建三个新属性：`Status`、`Assignee` 和 `Review Comments`。  我们在**“共享文档”**库中定义这些属性。  
  
#### 向 SharePoint 共享文档库中添加属性  
  
1.  在 Web 浏览器中打开一个 SharePoint 网站，如 http:\/\/\<系统名称\>\/SitePages\/Home.aspx。  
  
2.  在快速启动栏上选择**共享文档**。  
  
3.  在**“库工具”**功能区上选择**“库”**，然后选择该功能区上的**“创建列”**按钮以创建新列。  
  
4.  将该列命名为“文档状态”，将其类型设置为**“选项\(要从中选择的菜单\)”**，指定以下三个选项，然后选择**“确定”**按钮：  
  
    -   **需要评审**  
  
    -   **评审完成**  
  
    -   **请求更改**  
  
5.  再创建两列并将它们命名为“受理人”和“评审注释”。  将“受理人”列类型设置为单行文本，将“评审注释”列类型设置为多行文本。  
  
## 使文档无需签出即可编辑  
 如果无需签出文档即可进行编辑，则测试工作流模板会更容易一些。  在下一个过程中，您将配置 SharePoint 网站以达到此目的。  
  
#### 使文档无需签出即可编辑  
  
1.  选择快速启动栏上的**“共享文档”**链接。  
  
2.  在**“库工具”**功能区上选择**“库”**选项卡，然后选择**“库设置”**按钮以显示**“文档库设置”**页。  
  
3.  在**“常规设置”**部分中，选择**“版本控制设置”**链接以显示**“版本控制设置”**页。  
  
4.  验证**“要求先签出文档然后再对其进行编辑”**的设置是否为**“否”**。  如果不是这样，请将其更改为**“否”**，然后选择**“确定”**按钮。  
  
5.  关闭浏览器。  
  
## 创建 SharePoint 顺序工作流项目  
 顺序工作流是按顺序执行直到最后一个活动完成的一组步骤。  在此过程中，我们将创建一个将应用于“共享文档”列表的顺序工作流。  利用此工作流向导，您可以将工作流与网站定义或列表定义关联，并可以确定工作流的启动时间。  
  
#### 创建 SharePoint 顺序工作流项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**，以显示**“新建项目”**对话框。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 模板。  
  
5.  在**“名称”**框中，输入MySharePointWorkflow，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
6.  在 **指定用于调试的网站和安全级别** 页中，选择 **部署为场解决方案** 选项按钮，然后选择 **完成** 按钮以接受默认站点和信任级别。  
  
     此步骤会将解决方案的信任级别设置为场解决方案（工作流项目的唯一可用选项）。  有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在**“解决方案资源管理器”**中，选择项目节点，然后在菜单栏上选择**“项目”**，再选择**“添加新项”**。  
  
8.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
9. 在 **模板** 窗格中，选择 **顺序工作流 \(仅场解决方案\)** 模板，然后选择 **添加** 按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  
  
10. 在**“指定用于调试的工作流名称”**页上，接受默认名称（**“MySharePointWorkflow \- Workflow1”**）。  保留默认工作流模板类型值**“列表工作流”**，然后选择**“下一步”**按钮。  
  
11. 在**“是否希望 Visual Studio 在调试会话中自动关联工作流?”**页中，选择**“下一步”**按钮以接受所有默认设置。  
  
     此步骤会自动将工作流与共享文档库关联。  
  
12. 在**“指定确定工作流启动方式的条件”**页上，将**“您希望如何启动工作流?”**部分的默认选项保持选中状态，然后选择**“完成”**按钮。  
  
     可利用此页指定工作流启动的时间。  默认情况下，当用户在 SharePoint 中手动启动工作流时，或在创建与工作流关联的项时，工作流将启动。  
  
## 创建工作流活动  
 工作流包含一个或多个表示要执行的操作的活动。  使用工作流设计器可为工作流安排活动。  在此过程中，我们将向工作流中添加两个活动：HandleExternalEventActivity 和 OnWorkFlowItemChanged。  这些活动将监视**“共享文档”**列表中文档的评审状态。  
  
#### 创建工作流活动  
  
1.  工作流应显示在工作流设计器中。  如果不是这样，请打开**“解决方案资源管理器”**中的**“Workflow1.cs”**或**“Workflow1.vb”**。  
  
2.  在设计器中，选择**“OnWorkflowActivated1”**活动。  
  
3.  在**“属性”**窗口中，在**“Invoked”**属性旁键入 onWorkflowActivated，然后选择 Enter。  
  
     代码编辑器将会打开，一个名为“onWorkflowActivated”的事件处理程序方法被添加到 Workflow1 代码文件中。  
  
4.  切换回工作流设计器，打开工具箱，然后展开**“Windows Workflow v3.0”**节点。  
  
5.  在 **Windows Workflow v3.0工具箱**节点，请执行以下任意一组步骤：  
  
    1.  打开**While**活动的快捷菜单，然后选择**“复制”**。  在工作流设计器，打开 **onWorkflowActivated1** 活动下方的行快捷菜单，然后选择 **粘贴**。  
  
    2.  从**“工具箱”**拖动一个**While**活动到工作流设计器节点，并将该活动与**“onWorkflowActivated1”**活动下的行连接。  
  
6.  选择 **WhileActivity1** 活动。  
  
7.  在**“属性”**窗口中，将**“Condition”**设置为“代码定义”。  
  
8.  展开**“Condition”**属性，在**“Condition”**属性旁键入 isWorkflowPending，然后选择 Enter键。  
  
     代码编辑器将会打开，一个名为 isWorkflowPending 的方法被添加到 Workflow1 代码文件中。  
  
9. 切换回工作流设计器，打开工具箱，然后展开**“SharePoint 工作流”**节点。  
  
10. 在 **SharePoint 工作流工具箱**节点，请执行以下任意一组步骤：  
  
    -   打开**OnWorkflowItemChanged**活动的快捷菜单，然后选择**“复制”**。  在工作流设计器，打开 **whileActivity1** 活动中的行快捷菜单，然后选择 **粘贴**。  
  
    -   从**“工具箱”**拖动**OnWorkflowItemChanged**活动到工作流设计器，并将该活动与**whileActivity1**活动中的行连接。  
  
11. 选择 **onWorkflowItemChanged1** 活动。  
  
12. 在**“属性”**窗口中，如下表所示设置属性。  
  
    |Property|值|  
    |--------------|-------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## 处理活动事件  
 最后，检查每个活动后文档的状态。  如果文档已经过评审，则工作流将完成。  
  
#### 处理活动事件  
  
1.  在 Workflow1.cs 或 Workflow1.vb 中，将以下字段添加到 `Workflow1` 类的顶部。  在活动中使用此字段可确定工作流是否已完成。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  将下面的方法添加到 `Workflow1` 类中。  此方法检查“文档”列表的 `Document Status` 属性的值，以确定文档是否已评审。  如果 `Document Status` 属性设置为 `Review Complete`，`checkStatus` 方法就将 `workflowPending` 字段设置为 **false** 以指示工作流可以完成。  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  将下面的代码添加到 `onWorkflowActivated` 和 `onWorkflowItemChanged` 方法以调用 `checkStatus` 方法。  当工作流开始时，`onWorkflowActivated` 方法调用 `checkStatus` 方法以确定文档是否已评审。  如果文档尚未评审，则工作流继续。  保存文档时，`onWorkflowItemChanged` 方法再次调用 `checkStatus` 方法以确定文档是否已评审。  如果 `workflowPending` 字段设置为 **true**，则工作流继续运行。  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  向 `isWorkflowPending` 方法中添加以下代码以检查 `workflowPending` 属性的状态。  每次保存文档时，**“whileActivity1”**活动都会调用 `isWorkflowPending` 方法。  此方法检查 <xref:System.Workflow.Activities.ConditionalEventArgs> 对象的 <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> 属性，以确定**“WhileActivity1”**活动应继续还是完成。  如果该属性设置为 **true**，则活动继续。  否则，活动完成并且工作流也完成。  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  保存项目。  
  
## 测试 SharePoint 工作流模板  
 启动调试器时，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 将工作流模板部署到 SharePoint Server，并将该工作流与**“共享文档”**列表相关联。  若要测试工作流，请从**“共享文档”**列表中的某个文档启动工作流的一个实例。  
  
#### 测试 SharePoint 工作流模板  
  
1.  在 Workflow1.cs 或 Workflow1.vb 中，在**“onWorkflowActivated”**方法旁设置一个断点。  
  
2.  选择 F5 键生成并运行解决方案。  
  
     SharePoint 网站将出现。  
  
3.  在 SharePoint 中的导航窗格中选择**“共享文档”**链接。  
  
4.  在**“共享文档”**页中，选择**“库工具”**选项卡上的**“文档”**链接，然后选择**“上载文档”**按钮。  
  
5.  在 **上载文档** 对话框中，选择 **浏览** 按钮，选择任何文档文件，选择 **打开** 按钮，然后选择 **确定** 按钮。  
  
     这会将选定文档上载到**“共享文档”**列表中并启动工作流。  
  
6.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，确认调试器是否在 `onWorkflowActivated` 方法旁的断点处停止。  
  
7.  选择 F5 键继续执行。  
  
8.  虽然您可以在此处更改文档的设置，但此时请选择**“保存”**按钮以保留这些文档设置的默认值。  
  
     这将返回到默认 SharePoint 网站的**“共享文档”**页。  
  
9. 在**“共享文档”**页中，验证**“MySharePointWorkflow – Workflow1”**列下方的值是否设置为**“正在进行中”**。  这指示工作流正在进行中，文档在等待评审。  
  
10. 在 **共享文档** 页中，选择文档，选择将的箭头，然后选择 **编辑属性** 菜单项。  
  
11. 将**“文档状态”**设置为**“评审完成”**，然后选择**“保存”**按钮。  
  
     这将返回到默认 SharePoint 网站的**“共享文档”**页。  
  
12. 在**“共享文档”**页中，验证**Document Status**列下方的值是否设置为**“评审完成”**。  刷新**“共享文档”**页，并验证**“MySharePointWorkflow – Workflow1”**列下方的值是否设置为**“完成”**。  这指示工作流已完成，文档已评审。  
  
## 后续步骤  
 可从以下主题中了解有关如何创建工作流模板的更多信息：  
  
-   若要了解有关 SharePoint 工作流活动的更多信息，请参见 [SharePoint Foundation 的工作流活动](http://go.microsoft.com/fwlink/?LinkId=178992)。  
  
-   若要了解有关 Windows Workflow Foundation 活动的更多信息，请参见 [System.Workflow.Activities 命名空间](http://go.microsoft.com/fwlink/?LinkId=178993)。  
  
## 请参阅  
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  