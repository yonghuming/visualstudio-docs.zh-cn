---
title: "演练： 创建和调试 SharePoint 工作流解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d64c0767cce43d5b157fca82cc3e1e210a2f8c58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>演练：创建和调试 SharePoint 工作流解决方案
  本演练演示如何创建基本的顺序工作流模板。 工作流检查共享的文档库以确定是否已评审文档属性。 如果文档已评审，工作流完成。  
  
 本演练阐释了以下任务：  
  
-   创建 SharePoint 列表定义顺序工作流项目中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   创建工作流活动。  
  
-   处理工作流活动事件。  
  
> [!NOTE]  
>  虽然本演练中使用的顺序工作流项目，但过程是相同的状态机工作流项目。  
>   
>  此外，你的计算机可能不同的名称或位置的某些 Visual Studio 用户界面元素出现以下说明中。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>将属性添加到 SharePoint 共享的文档库  
 跟踪中的文档的查看状态**共享文档**库，我们将在我们的 SharePoint 站点上创建的共享文档的三个新属性： `Status`， `Assignee`，和`Review Comments`。 我们定义中的这些属性**共享文档**库。  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>将属性添加到共享的 SharePoint 文档库  
  
1.  打开 SharePoint 网站，如 http://\<系统名称 > / SitePages/Home.aspx，在 Web 浏览器中的。  
  
2.  在快速启动栏上，选择**SharedDocuments**。  
  
3.  选择**库**上**库工具**功能区，然后选择**创建列**功能区创建新的列上的按钮。  
  
4.  名称列**文档状态**，将其类型设置为**选择 （菜单可选择从）**，指定以下三个选项，然后选择**确定**按钮：  
  
    -   **需要评审**  
  
    -   **查看完成**  
  
    -   **更改请求**  
  
5.  创建两个更多列，并将它们命名**受托人**和**评审评论**。 将作为单独的一行文本的受托人列类型和，，请参见注释列类型设置为多行文本。  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>启用要进行编辑而无需签出文档  
 很容易地测试工作流模板，你可以编辑的文档，而无需签出时。在下一步的过程中，你可以配置 SharePoint 站点以进行此操作。  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>若要启用要编辑但不签出文档  
  
1.  在快速启动栏上，选择**共享文档**链接。  
  
2.  上**库工具**功能区上，选择**库**选项卡上，然后选择**库设置**按钮以显示**文档库设置**页。  
  
3.  在**常规设置**部分中，选择**版本控制设置**链接以显示**版本控制设置**页。  
  
4.  验证的设置**需要签出之前可以编辑这些文档**是**否**。 如果不是这样，将其更改为**否**，然后选择**确定**按钮。  
  
5.  关闭浏览器。  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>创建 SharePoint 顺序工作流项目  
 顺序工作流是一组步骤，直到完成的最后一个活动是按顺序执行。 在此过程中，我们将创建将应用于我们的共享文档列表的顺序工作流。 工作流向导可将工作流与站点定义或列表定义相关联，并使你能够确定工作流何时开始。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>若要创建 SharePoint 顺序工作流项目  
  
1.  启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，选择**文件**，**新建**，**项目**以显示**新项目**对话框。  
  
3.  展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**节点。  
  
4.  在**模板**窗格中，选择**SharePoint 2010 项目**模板。  
  
5.  在**名称**框中，输入**MySharePointWorkflow** ，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
6.  在**指定用于调试的站点和安全性级别**页上，选择**部署为场解决方案**选项按钮，，然后选择**完成**按钮以接受信任级别和默认站点。  
  
     此步骤将解决方案的信任级别设置为场解决方案，工作流项目的唯一可用的选项。 有关详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在**解决方案资源管理器**，选择项目节点，然后，在菜单栏上，选择**项目**，**添加新项**。  
  
8.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**节点。  
  
9. 在**模板**窗格中，选择**顺序工作流 （仅场解决方案）**模板，然后选择**添加**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
10. 在**指定用于调试的工作流名称**页上，接受默认名称 (**MySharePointWorkflow-Workflow1**)。 保留默认工作流模板的类型值中，**列表工作流**，然后选择**下一步**按钮。  
  
11. 在**想让 Visual Studio 以自动将工作流关联的调试会话中？**页上，选择**下一步**按钮以接受所有默认设置。  
  
     此步骤将工作流与共享文档库自动关联。  
  
12. 在**指定为工作流的启动方式的条件**页上，保留默认选项中选择**你希望如何启动工作流？**部分并选择**完成**按钮。  
  
     此页可以指定当工作流启动。 默认情况下，工作流将启动时在用户手动启动它在 SharePoint 或当创建工作流所关联到一个项。  
  
## <a name="creating-workflow-activities"></a>创建工作流活动  
 工作流包含一个或多*活动*，可表示要执行的操作。 工作流设计器用于将活动安排的工作流。 在此过程中，我们将向工作流中添加两个活动： HandleExternalEventActivity 和 OnWorkFlowItemChanged。 这些活动监视中的文档的查看状态**共享文档**列表  
  
#### <a name="to-create-workflow-activities"></a>若要创建工作流活动  
  
1.  工作流应显示在工作流设计器。 如果不是这样，然后打开**Workflow1.cs**或**Workflow1.vb**中**解决方案资源管理器**。  
  
2.  在设计器中，选择**OnWorkflowActivated1**活动。  
  
3.  在**属性**窗口中，输入**onWorkflowActivated**旁边**调用**属性，然后选择 Enter 键。  
  
     代码编辑器将打开，并且名为 onWorkflowActivated 的事件处理程序方法添加到 Workflow1 代码文件。  
  
4.  切换回工作流设计器，打开工具箱，然后展开**Windows Workflow v3.0**节点。  
  
5.  在**Windows Workflow v3.0**节点**工具箱**，执行以下步骤集之一：  
  
    1.  打开的快捷菜单**时**活动，然后选择**复制**。 在工作流设计器中，打开的行的快捷菜单**onWorkflowActivated1**活动，然后选择**粘贴**。  
  
    2.  拖动**时**活动从**工具箱**到工作流设计器，并连接到下的行的活动**onWorkflowActivated1**活动。  
  
6.  选择**WhileActivity1**活动。  
  
7.  在**属性**窗口中，设置**条件**到代码条件。  
  
8.  展开**条件**属性，输入**isWorkflowPending**旁边子**条件**属性，然后选择 Enter 键。  
  
     代码编辑器随即打开，和一个名为 isWorkflowPending 方法添加到 Workflow1 代码文件。  
  
9. 切换回工作流设计器，打开工具箱，然后展开**SharePoint 工作流**节点。  
  
10. 在**SharePoint 工作流**节点**工具箱**，执行以下步骤集之一：  
  
    -   打开的快捷菜单**OnWorkflowItemChanged**活动，然后选择**复制**。 在工作流设计器中，打开中的一行的快捷菜单**whileActivity1**活动，然后选择**粘贴**。  
  
    -   拖动**OnWorkflowItemChanged**活动从**工具箱**到工作流设计器，并将该活动连接到中的一行**whileActivity1**活动。  
  
11. 选择**onWorkflowItemChanged1**活动。  
  
12. 在**属性**窗口中，设置的属性下, 表中所示。  
  
    |属性|值|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**调用**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>处理活动事件  
 最后，检查从每个活动文档的状态。 如果已评审文档，然后完成工作流。  
  
#### <a name="to-handle-activity-events"></a>若要处理活动事件  
  
1.  在 Workflow1.cs 或 Workflow1.vb，将以下字段添加到顶部`Workflow1`类。 此字段在活动中用于确定是否已完成工作流。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  将以下方法添加到 `Workflow1` 类。 此方法检查的值`Document Status`要确定是否已评审文档的文档列表的属性。 如果`Document Status`属性设置为`Review Complete`，则`checkStatus`方法设置`workflowPending`字段**false**以指示工作流已准备好完成。  
  
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
  
3.  以下代码添加到`onWorkflowActivated`和`onWorkflowItemChanged`方法来调用`checkStatus`方法。 当工作流开始，则`onWorkflowActivated`方法调用`checkStatus`方法来确定文档是否已评审。 如果它没有经过审核，则工作流继续。 保存文档后，`onWorkflowItemChanged`方法调用`checkStatus`方法再次以确定是否已评审文档。 虽然`workflowPending`字段设置为**true**，工作流继续运行。  
  
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
  
4.  以下代码添加到`isWorkflowPending`方法来检查的状态`workflowPending`属性。 保存文档后，每次**whileActivity1**活动调用`isWorkflowPending`方法。 此方法检查<xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A>属性<xref:System.Workflow.Activities.ConditionalEventArgs>对象以确定是否**WhileActivity1**活动应继续还是完成。 如果该属性设置为**true**，则活动继续。 否则为在活动完成，并且工作流完成。  
  
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
  
## <a name="testing-the-sharepoint-workflow-template"></a>测试 SharePoint 工作流的模板  
 当您启动调试器，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将工作流模板部署到 SharePoint 服务器并将关联的工作流**共享文档**列表。 若要测试工作流，启动工作流实例中的文档从**共享文档**列表。  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>若要测试 SharePoint 工作流模板  
  
1.  在 Workflow1.cs 或 Workflow1.vb，设置一个断点旁边**onWorkflowActivated**方法。  
  
2.  选择 F5 生成并运行解决方案。  
  
     SharePoint 站点会显示。  
  
3.  在 SharePoint 中的导航窗格中，选择**共享文档**链接。  
  
4.  在**共享文档**页上，选择**文档**链接**库工具**选项卡上，然后选择**上载文档**按钮.  
  
5.  在**上载文档**对话框框中，选择**浏览**按钮，选择任何文档文件，选择**打开**按钮，，然后选择**确定**按钮。  
  
     这将上载到选定的文档**共享文档**列表中并启动工作流。  
  
6.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，验证，调试器将停止在断点处旁边`onWorkflowActivated`方法。  
  
7.  选择 F5 键以继续执行。  
  
8.  你可以更改在这里，该文档的设置但使其保持为默认值现在通过选择**保存**按钮。  
  
     此操作将返回到**共享文档**默认 SharePoint 网站的页。  
  
9. 在**共享文档**页上，确认下面的值**MySharePointWorkflow-Workflow1**列设置为**正在进行中**。 这指示工作流正在进行，文档在等待评审。  
  
10. 在**共享文档**页上，选择该文档，选择的箭头，会显示，，然后选择**编辑属性**菜单项。  
  
11. 设置**文档状态**到**评审完成**，然后选择**保存**按钮。  
  
     此操作将返回到**共享文档**默认 SharePoint 网站的页。  
  
12. 在**共享文档**页上，确认下面的值**文档状态**列设置为**评审完成**。 刷新**共享文档**页上，并验证下面的值**MySharePointWorkflow-Workflow1**列设置为**已完成**。 这指示工作流已完成和已检查文档的信息。  
  
## <a name="next-steps"></a>后续步骤  
 你可以了解有关如何从下面这些主题中创建工作流模板的详细信息：  
  
-   若要了解有关 SharePoint 工作流活动的详细信息，请参阅[SharePoint Foundation 的工作流活动](http://go.microsoft.com/fwlink/?LinkId=178992)。  
  
-   若要了解有关 Windows Workflow Foundation 活动的详细信息，请参阅[System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993)。  
  
## <a name="see-also"></a>另请参阅  
 [创建 SharePoint 工作流解决方案](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  