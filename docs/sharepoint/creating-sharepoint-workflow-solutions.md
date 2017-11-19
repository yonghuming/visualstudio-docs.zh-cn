---
title: "创建 SharePoint 工作流解决方案 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 256eaf2b451f91abdcc90c2beeedb7f689e95db6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-sharepoint-workflow-solutions"></a>创建 SharePoint 工作流解决方案
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供工具以帮助您创建自定义管理生命周期的文档和 SharePoint 网站中的列表项的工作流。 提供的项包括设计器、一组活动控件以及必需的程序集引用。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]此外包括**SharePoint 自定义向导**来帮助创建和配置工作流。  
  
 有关用于创建 SharePoint 项目中的必备组件列表[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。 有关 SharePoint 的详细信息，请参阅[Microsoft SharePoint 产品和技术](http://go.microsoft.com/fwlink/?LinkId=178470)。  
  
## <a name="workflows-in-sharepoint"></a>在 SharePoint 中的工作流  
 当你将工作流添加到 SharePoint 库或列表时，则强制执行业务流程中的库或列表的所有项上。 工作流描述了系统或用户必须在每个项，如发送要进行编辑，然后查看的项执行的操作。 这些操作，称为*活动*，是工作流的构建基块。  
  
 你可以创建 SharePoint 工作流中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]并将其部署到 SharePoint 网站。 工作流部署到 SharePoint 后，你将其与关联的库或列表。 它可以然后自动启动，手动，由进程或用户。 有关工作流操作的详细信息，请参阅[使用工作流管理过程](http://go.microsoft.com/fwlink/?LinkId=79757)。  
  
## <a name="creating-custom-sharepoint-workflows"></a>创建自定义 SharePoint 工作流  
 两个 SharePoint 工作流项目可供你在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]:**顺序工作流**和**状态机工作流**。  
  
 A*顺序工作流*表示一系列步骤。 执行这些步骤依次直到完成的最后一个活动。 顺序工作流始终是严格按顺序执行的。 因为它们可以接收外部事件，并且包含并行逻辑流，确切的执行顺序可能会有所不同。 下图显示的顺序工作流的示例。  
  
 ![顺序工作流](../sharepoint/media/sp-sequential.png "顺序工作流")  
  
 A*状态机工作流*表示一组的状态、 转换和操作。 状态机工作流中的步骤以异步方式执行。 这意味着它们不一定执行，但改为触发由操作和状态。 一个状态被指定为起始状态，然后，根据事件，转换会对另一个状态进行。 状态机可以有最终状态，确定工作流末尾。 下图显示的状态机工作流的示例。  
  
 ![状态机工作流](../sharepoint/media/sp-state.png "状态机工作流")  
  
 有关工作流类型的详细信息，请参阅[工作流类型](http://go.microsoft.com/fwlink/?LinkId=178995)。  
  
### <a name="using-the-wizard"></a>使用向导  
 当创建中的 SharePoint 工作流项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，首先指定在其设置**SharePoint 自定义向导**。 向导将使用这些设置中创建一个项目**解决方案资源管理器**。 此项目包含一个代码文件，用于部署工作流的多个文件，并创建自定义的 SharePoint 工作流所需的程序集引用。  
  
 创建工作流后，你可以修改其属性在属性窗口中。 尽管可以直接在属性窗口中更改大多数工作流属性，但一些要求你单击省略号按钮 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆")) 到更改它们的值。 此按钮将重新启动**SharePoint 自定义向导**。 将值更改时，请选择该属性后**完成**按钮来完成。  
  
> [!NOTE]  
>  **工作流类型**属性是只读的并且不能更改。 如果你想要更改工作流类型，则必须创建另一个工作流。  
  
## <a name="designing-a-sharepoint-workflow"></a>设计 SharePoint 工作流  
 在业务流程中定义的所有步骤后，使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流设计器设计 SharePoint 工作流。 若要打开设计器，请双击 Workflow1.cs 或 Workflow1.vb 中的**解决方案资源管理器**，或为这些文件的打开的快捷菜单，然后选择**打开**。  
  
### <a name="activities"></a>活动  
 若要设计工作流，请将活动从添加**工具箱**到*工作流计划*设计器上。 工作流计划包含应执行它们的顺序中的活动序列。  
  
 有两种类型的活动：  
  
-   *简单活动*执行单个工作单元，如"延迟 1 天"或"启动 Web 服务。  
  
-   *复合活动*包含其他活动; 例如，条件的活动可能包含两个分支。  
  
 这两种类型的活动均位于**工具箱**。  
  
 活动可以有属性、 方法和事件。 使用**属性**窗口设置活动的属性。  
  
 你还可以创建自定义活动。 有关详细信息，请参阅[演练： 创建自定义网站工作流活动](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)。  
  
 活动组织中的以下选项卡**工具箱**:  
  
-   **SharePoint 工作流**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 并非所有核心工作流活动都支持 SharePoint。 有关详细信息，请参阅[工作流活动的 Windows SharePoint Services 概述](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### <a name="sharepoint-workflow-activities"></a>SharePoint 工作流活动  
 **SharePoint 工作流**选项卡包含在中使用的特殊的活动[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]。 这些活动可简化，简化的文档生命周期工作流开发。 有关中列出的活动详细信息**SharePoint 工作流**选项卡上，请参阅[工作流活动的 Windows SharePoint Services 概述](http://go.microsoft.com/fwlink/?LinkID=156094)。  
  
#### <a name="windows-workflow-activities"></a>Windows 工作流活动  
 **Windows 工作流**选项卡包含由提供的活动[!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]。 这些活动可用于创建 Windows 工作流应用程序的任何类型的工作流计划。  
  
 有关中列出的活动详细信息**Windows 工作流**选项卡上，请参阅[Windows Workflow Foundation 活动](http://go.microsoft.com/fwlink/?LinkID=156096)。 有关 Windows Workflow Foundation 的详细信息，请参阅[Windows Workflow Foundation 概述](http://go.microsoft.com/fwlink/?LinkID=128632)。  
  
### <a name="working-with-activities-in-the-designer"></a>处理活动设计器中  
 你的工作流计划可以包含 Windows 工作流活动和 SharePoint 工作流活动的组合。  
  
 设计器显示可视提示来帮助您定位和正确配置活动。 当您将活动拖动或复制到工作流时间表上时，设计器会显示绿色加号 (+) 图标，为您指示该活动在工作流中的有效位置。 也不能将活动放置在其中但却不是有效的位置。 例如，您不能在侦听活动分支中放置发送活动的第一个活动。 有关详细信息，请参阅[SharePoint Designer 开发人员中心](http://go.microsoft.com/fwlink/?LinkId=178476)。  
  
## <a name="collecting-information-during-the-workflow"></a>工作流过程中收集的信息  
 你可能想要从用户收集信息在预定义的工作流中的时间。 可以通过使用窗体或项目属性来收集信息。  
  
### <a name="forms"></a>窗体  
 窗体是类似于包含问题并提供为用户提供答案的方法的对话框。  
  
 有四种类型的可以在工作流中使用的窗体：  
  
-   关联  
  
-   启动  
  
-   修改  
  
-   任务  
  
 其中，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包括关联和启动窗体的项模板。 一个示例*关联窗体*可安装工作流的管理员正在输入与工作流，如支出限制费用工作流相关的参数。 一个示例*启动窗体*是指供费用工作流金额输入工作流的用户。 有关这些类型的窗体的详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
### <a name="item-properties"></a>项目属性  
 此外可以通过使用 SharePoint 库或列表中的项的属性，从用户中收集信息。 名为的 Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties 类的实例的主代码文件 （Workflow1.cs 或 Workflow1.vb） 声明`workflowProperties`。 使用`workflowProperties`对象来访问的库或在代码中的列表的属性。 有关示例，请参阅[演练： 创建和调试 SharePoint 工作流解决方案](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)。  
  
## <a name="debugging-a-sharepoint-workflow-template"></a>调试 SharePoint 工作流模板  
 你可以调试 SharePoint 工作流项目相同如调试其他[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]基于 Web 的项目。 当你启动[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]调试器，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用你在中指定的设置**SharePoint 自定义向导**以打开相应的 SharePoint 网站，并自动将工作流模板相关联与相应的库或列表。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]此外会将附加[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]到调试器[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]名为 w3wp.exe 进程。  
  
 若要测试工作流，必须手动启动它。 详细信息，请参阅"调试工作流"一节中[调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)。 有关详细信息[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Web 应用程序调试，请参阅[调试 Web 应用程序和脚本](/visualstudio/debugger/debugging-web-applications-and-script)。  
  
## <a name="deploying-a-sharepoint-workflow-template"></a>部署 SharePoint 工作流模板  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]就像其他部署 SharePoint 工作流项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。 有关详细信息，请参阅[打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)。  
  
## <a name="importing-globally-reusable-workflows"></a>导入全局可重用工作流  
 除了创建特定于站点的可重用工作流，SharePoint 设计器使您能够创建*全局可重用工作流*，这是工作流，可由任何 SharePoint 站点使用。 中的导入可重用工作流项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]当前不导入全局可重用工作流。 但是，你可以使用 SharePoint Designer 将全局可重用工作流转换为可重用工作流，或导入作为未转换的声明性工作流的工作流。 有关详细信息，请参阅[从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[演练：创建和调试 SharePoint 工作流解决方案](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|将引导你逐步完成创建和调试一个简单[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]工作流。|  
|[演练：创建带有关联窗体和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|指导你逐步创建功能更全面的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的关联和启动窗体的工作流完成。|  
|[演练：将应用程序页添加到工作流](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|基于主题[演练： 创建带有关联和启动窗体的工作流](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)通过添加报告数据输入到工作流的其他.aspx 应用程序页。|  
|[演练：创建自定义站点工作流活动](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|演示如何执行两项关键任务： 创建站点级别的工作流，并创建自定义工作流活动。|  
|[演练：将 SharePoint Designer 可重用工作流导入 Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|演示如何导入可重用声明性工作流在 SharePoint Designer 2010 到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。|  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [生成和调试 SharePoint 解决方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  