---
title: "演练：在运行时更新功能区上的控件"
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
  - "控件 [Visual Studio 中的 Office 开发], 功能区"
  - "动态菜单 [Visual Studio 中的 Office 开发]"
  - "功能区 [Visual Studio 中的 Office 开发], 控件"
  - "功能区 [Visual Studio 中的 Office 开发], 动态菜单"
  - "功能区 [Visual Studio 中的 Office 开发], 更新"
  - "更新功能区控件"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 演练：在运行时更新功能区上的控件
  本演练演示了如何使用功能区对象模型在功能区加载到 Office 应用程序之后，更新该功能区上的控件。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 此示例提取来自 Northwind 示例数据库的数据，以填充 Microsoft Office Outlook 中的组合框和菜单。  你在这些控件中选择的项将自动填充字段，例如电子邮件中的**“收件人”**和**“主题”**。  
  
 本演练阐释了以下任务：  
  
-   创建新的 Outlook VSTO 外接程序项目。  
  
-   设计自定义功能区组。  
  
-   将自定义组添加到内置选项卡。  
  
-   在运行时更新功能区上的控件。  
  
> [!NOTE]  
>  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## 创建新的 Outlook VSTO 外接程序项目  
 首先，创建 Outlook VSTO 外接程序项目。  
  
#### 创建新的 Outlook VSTO 外接程序项目  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，创建名为 Ribbon\_Update\_At\_Runtime 的 Outlook VSTO 外接程序项目。  
  
2.  在**“新建项目”**对话框中，选择**“创建解决方案的目录”**。  
  
3.  将项目保存到默认项目目录中。  
  
     有关详细信息，请参阅[如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## 设计自定义功能区组  
 当用户撰写一封新邮件消息时，将显示此示例中的功能区。  若要为功能区创建自定义组，请首先向项目中添加一个功能区项，然后在功能区设计器中设计组。  通过此自定义组，可从数据库中拉取名称和订单历史记录，从而生成要发送给客户的后续电子邮件消息。  
  
#### 设计自定义组  
  
1.  在**“项目”**菜单上，单击**“添加新项”**。  
  
2.  在**“添加新项”**对话框中，选择**“功能区\(可视化设计器\)”**。  
  
3.  将新功能区更名为 **CustomerRibbon**，然后单击**“添加”**。  
  
     **CustomerRibbon.cs** 或 **CustomerRibbon.vb** 文件将在功能区设计器中打开，并显示一个默认选项卡和组。  
  
4.  单击功能区设计器以将其选定。  
  
5.  在**“属性”**窗口中，单击**“RibbonType”**属性旁边的下拉箭头，然后单击**“Microsoft.Outlook.Mail.Compose”**。  
  
     这样，当用户在 Outlook 中撰写新的邮件消息时，将显示该功能区。  
  
6.  在功能区设计器中，单击**“Group1”**以将其选中。  
  
7.  在**“属性”**窗口中，将**“标签”**设置为“客户采购”。  
  
8.  从**“工具箱”**的**“Office 功能区控件”**选项卡中，将**“组合框”**拖到**“客户采购”**组上。  
  
9. 单击**“ComboBox1”**以将其选中。  
  
10. 在**“属性”**窗口中，将**“标签”**设置为“客户”。  
  
11. 从**“工具箱”**的**“Office 功能区控件”**选项卡中，将**“菜单”**拖到**“客户采购”**组上。  
  
12. 在**“属性”**窗口中，将**“标签”**设置为“已采购产品”。  
  
13. 将**“动态”**设置为 **true**。  
  
     这样，在功能区加载到 Office 应用程序中之后，就可以在运行时添加和删除菜单上的控件。  
  
## 将自定义组添加到内置选项卡  
 内置选项卡是指 Outlook 浏览器或检查器的功能区上已经存在的选项卡。  在此过程中，将自定义组添加到内置选项卡，然后指定自定义组在选项卡上的位置。  
  
#### 将自定义组添加到内置选项卡  
  
1.  单击**“TabAddins \(内置\)”**选项卡以将其选中。  
  
2.  在**“属性”**窗口中，展开**“ControlId”**属性，然后将**“OfficeId”**设置为“TabNewMailMessage”。  
  
     这会将**“客户采购”**组添加到新邮件消息中出现的功能区上的**“消息”**选项卡中。  
  
3.  单击**“客户采购”**组以将其选中。  
  
4.  在**“属性”**窗口中，展开**“Position”**属性，单击**“PositionType”**属性旁边的下拉箭头，然后单击**“BeforeOfficeId”**。  
  
5.  将**“OfficeId”**属性设置为“GroupClipboard”。  
  
     这会将**“客户采购”**组放置在**“消息”**选项卡上**“剪贴板”**组的前面。  
  
## 创建数据源  
 使用**“数据源”**窗口将类型化数据集添加到项目中。  
  
#### 创建数据源  
  
1.  在**“数据”**菜单上，单击**“添加新数据源”**。  
  
     这将启动**“数据源配置向导”**。  
  
2.  选择**“数据库”**，然后单击**“下一步”**。  
  
3.  选择**“数据集”**，然后单击**“下一步”**。  
  
4.  选择与 Northwind 示例 Microsoft SQL Server Compact 4.0 数据库的数据连接，或使用**“新建连接”**按钮添加新的连接。  
  
5.  选择或创建连接后，单击**“下一步”**。  
  
6.  单击**“下一步”**以保存连接字符串。  
  
7.  在**“选择数据库对象”**页上，展开**“表格”**。  
  
8.  选中以下每个表格旁的复选框：  
  
    1.  **Customers**  
  
    2.  **Order Details**  
  
    3.  **Orders**  
  
    4.  **产品**  
  
9. 单击**“完成”**。  
  
## 在运行时更新自定义组中的控件  
 使用功能区对象模型执行以下任务：  
  
-   将客户名称添加到**“客户”**组合框中。  
  
-   将菜单和按钮控件添加到表示销售订单和已售产品的**“已采购产品”**菜单中。  
  
-   使用**“客户”**组合框和**“已采购产品”**菜单中的数据填充新邮件消息的 To、Subject 和 Body 字段。  
  
#### 使用功能区对象模型更新自定义组中的控件  
  
1.  在**“项目”**菜单上，单击**“添加引用”**。  
  
2.  在**“添加引用”**对话框中，单击**“.NET”**选项卡，选择**“System.Data.Linq”**程序集，然后单击**“确定”**。  
  
     此程序集包含有关使用语言集成查询 \(LINQ\) 的类。  你将通过 LINQ 使用 Northwind 数据库中的数据填充自定义组中的控件。  
  
3.  在**“解决方案资源管理器”**中，单击**“CustomerRibbon.cs”**或**“CustomerRibbon.vb”**以将其选中。  
  
4.  在**“视图”**菜单中，单击**“代码”**。  
  
     功能区代码文件将在代码编辑器中打开。  
  
5.  将下面的语句添加到功能区代码文件的顶部。  通过执行这些语句，可轻松访问 LINQ 命名空间和 Outlook 主互操作程序集 \(PIA\) 的命名空间。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  将以下代码添加到 CustomerRibbon 类中。  此代码声明了将用于存储 Northwind 数据库的“客户”、“订单”、“订单明细”和“产品”表中信息的数据表和表适配器。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  将以下代码块添加到 `CustomerRibbon` 类中。  此代码添加 3 个可在运行时为功能区创建控件的帮助程序方法。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  将 `CustomerRibbon_Load` 事件处理程序方法替换为以下代码。  此代码使用 LINQ 查询执行以下任务：  
  
    -   通过使用 Northwind 数据库中 20 位客户的 ID 和名称，填充**“客户”**组合框。  
  
    -   调用 `PopulateSalesOrderInfo` 帮助程序方法。  此方法使用与当前所选客户相关的销售订单号更新**“ProductsPurchased”**菜单。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. 向 `CustomerRibbon` 类添加下面的代码。  此代码使用 LINQ 查询执行以下任务：  
  
    -   将子菜单添加到与所选客户相关的每个销售订单的**“ProductsPurchased”**菜单。  
  
    -   将按钮添加到与销售订单相关的产品的每个子菜单中。  
  
    -   将事件处理程序添加到每个按钮。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. 在**“解决方案资源管理器”**中，双击功能区代码文件。  
  
     功能区设计器随即打开。  
  
11. 在功能区设计器中，双击**“客户”**组合框。  
  
     功能区代码文件将在代码编辑器中打开，并且将显示 `ComboBox1_TextChanged` 事件处理程序。  
  
12. 将 `ComboBox1_TextChanged` 事件处理程序替换为以下代码。  这段代码执行下列任务：  
  
    -   调用 `PopulateSalesOrderInfo` 帮助程序方法。  此方法使用与所选客户相关的销售订单更新**“已采购产品”**菜单。  
  
    -   调用 `PopulateMailItem` 帮助程序方法并传入当前文本，该文本是所选客户名称。  此方法填充新邮件消息的 To、Subject 和 Body 字段。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. 将以下单击事件处理程序添加到 `CustomerRibbon` 类。  此代码将所选产品的名称添加到新邮件消息的 Body 字段。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. 向 `CustomerRibbon` 类添加下面的代码。  这段代码执行下列任务：  
  
    -   通过使用当前所选客户的电子邮件地址，填充新邮件消息的 To 行。  
  
    -   将文本添加到新邮件消息的 Subject 和 Body 字段。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## 测试自定义组中的控件  
 从 Outlook 中打开新邮件时，将在功能区的**“消息”**选项卡上显示名为**“客户采购”**的自定义组。  
  
 若要创建客户的后续电子邮件消息，请选择一位客户，然后选择该客户采购的产品。  在运行时，**“客户采购”**组中的控件使用 Northwind 数据库中的数据进行更新。  
  
#### 测试自定义组中的控件  
  
1.  按 F5 运行项目。  
  
     Outlook 启动。  
  
2.  在 Outlook 中的**“文件”**菜单上，指向**“新建”**，然后单击**“邮件消息”**。  
  
     将出现以下操作：  
  
    -   出现新的邮件消息检查器窗口。  
  
    -   在功能区的**“消息”**选项卡上，**“客户采购”**组位于**“剪贴板”**组的前面。  
  
    -   组中的**“客户”**组合框使用 Northwind 数据库中的客户名称进行更新。  
  
3.  在功能区**“消息”**选项卡上的**“客户采购”**组中，从**“客户”**组合框中选择客户。  
  
     将出现以下操作：  
  
    -   **“已采购产品”**菜单进行更新，以显示所选客户的每笔销售订单。  
  
    -   每笔销售订单子菜单进行更新，以显示该笔订单中购买的产品。  
  
    -   所选客户的电子邮件地址将添加到电子邮件消息的**“收件人”**行，并且邮件消息的主题和正文使用文本进行填充。  
  
4.  单击**“产品采购”**菜单，指向任一销售订单，然后单击该订单中的产品。  
  
     该产品名称将添加到邮件消息的正文中。  
  
## 后续步骤  
 可从以下主题了解有关如何自定义 Office 用户界面的更多信息：  
  
-   将基于上下文的 UI 添加到任何文档级自定义项。  有关详细信息，请参阅[操作窗格概述](../vsto/actions-pane-overview.md)。  
  
-   扩展标准的或自定义的 Microsoft Office Outlook 窗体。  有关详细信息，请参阅[演练：设计 Outlook 窗体区域](../vsto/walkthrough-designing-an-outlook-form-region.md)。  
  
-   将自定义任务窗格添加到 Outlook。  有关详细信息，请参阅[自定义任务窗格](../vsto/custom-task-panes.md)。  
  
## 请参阅  
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [功能区概述](../vsto/ribbon-overview.md)   
 [语言集成查询 \(LINQ\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [功能区对象模型概述](../vsto/ribbon-object-model-overview.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：更改功能区上选项卡的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：向 Backstage 视图添加控件](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：将功能区从功能区设计器导出为功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  