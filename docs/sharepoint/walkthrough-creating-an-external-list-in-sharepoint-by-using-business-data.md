---
title: "演练：使用业务数据在 SharePoint 中创建外部列表"
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
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发]，Web 部件中的业务数据"
  - "BDC [Visual Studio 中的 SharePoint 开发]，外部列表"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发]，SharePoint 列表中的业务数据"
  - "BDC [Visual Studio 中的 SharePoint 开发]，SharePoint 列表中的业务数据"
  - "BDC [Visual Studio 中的 SharePoint 开发]，Web 部件中的业务数据"
  - "BDC [Visual Studio 中的 SharePoint 开发]，支持的实体列表"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发]，支持的实体列表"
  - "业务数据连接服务 [Visual Studio 中的 SharePoint 开发]，外部列表"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 演练：使用业务数据在 SharePoint 中创建外部列表
  通过业务数据连接 \(BDC\) 服务，SharePoint 可以显示来自后端服务器应用程序、Web 服务和数据库的业务数据。  
  
 本演练演示如何为返回示例数据库中联系人相关信息的 BDC 服务创建模型。  然后，使用此模型在 SharePoint 中创建外部列表。  
  
 本演练阐释了以下任务：  
  
-   创建项目。  
  
-   向模型中添加实体。  
  
-   添加 Finder 方法。  
  
-   添加特定的 Finder 方法。  
  
-   测试项目。  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]、[!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] 或 [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]。  
  
-   对 AdventureWorks 示例数据库的访问权限。  有关如何安装 SQL Server 示例数据库 AdventureWorks 的更多信息，请参见[SQL Server Sample Databases](http://go.microsoft.com/fwlink/?LinkID=117483)。  
  
## 创建一个包含 BDC 模型的项目  
  
#### 创建一个包含 BDC 模型的项目  
  
1.  在 Visual Studio 的菜单栏上，依次选择**“文件”**、**“新建”**、**“项目”**。  
  
     **“新建项目”**对话框随即打开。  
  
2.  在**“Visual C\#”**或**“Visual Basic”**下，展开**“SharePoint”**节点，然后选择**“2010”**项。  
  
3.  在“模板” 窗格中，选择“SharePoint 2010 项目”，将项目命名为AdventureWorksTest，然后选择“确定”按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  此向导可以指定用于调试项目的站点以及解决方案并设置信任级别。  
  
4.  选择 “部署为场解决方案” 选项按钮设置信任级别。  
  
5.  选择“完成”按钮接受默认的本地 SharePoint 站点。  
  
6.  在“解决方案资源管理器”中，选择SharePoint项目节点。  
  
7.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
     **“添加新项”**对话框打开。  
  
8.  在 “模板” 窗格中，选择 ”业务数据连接模型 \(仅场解决方案\)“，将项目命名为 AdventureWorksContacts，然后选择 ”添加“ 按钮。  
  
## 向项目添加数据访问类  
  
#### 向项目添加数据访问类  
  
1.  在菜单栏上选择“工具”菜单上，“连接到数据库”。  
  
     **“添加连接”**对话框随即打开。  
  
2.  添加一个到 SQL Server AdventureWorks 示例数据库的连接。  
  
     有关详细信息，请参阅[Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/zh-cn/fa400910-26c3-4df7-b9d1-115e688b4ea3)。  
  
3.  在**“解决方案资源管理器”**中，选择项目节点。  
  
4.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
5.  在“已安装的模板”窗格中，选择“数据”节点。  
  
6.  在“模板”窗格中，选择“LINQ to SQL 类”。  
  
7.  在“名称”框中指定AdventureWorks，然后选择“添加”按钮。  
  
     .dbml 文件会添加到项目中，并打开对象关系设计器（O\/R 设计器）。  
  
8.  在菜单栏上，依次选择**“视图”**、**“服务器资源管理器”**  
  
9. 在**“服务器资源管理器”**中，展开代表 AdventureWorks 示例数据库的节点，然后展开**“表”**节点。  
  
10. 将“Contact\(Person\)”表拖到 O\/R 设计器上。  
  
     一个实体类将创建并显示在设计图面上。  该实体类的属性映射到“Contact\(Person\)”表的列。  
  
## 从 BDC 模型中删除默认实体  
 **“业务数据连接模型”**项目向模型中添加一个名为 Entity1 的默认实体。  移除此实体。  然后添加一个新的实体。  以空模型作为入手点可以减少完成本演练所需的步骤数。  
  
#### 从模型中移除默认实体  
  
1.  在**“解决方案资源管理器”**中，展开**“BdcModel1”**节点，然后打开“BdcModel1.bdcm”文件。  
  
2.  业务数据连接模型文件将在 BDC 设计器中打开。  
  
3.  在屏幕设计器中，打开“Entity1”节点的快捷菜单，然后选择“删除”。  
  
4.  在 ”解决方案资源管理器“中，打开 Entity1.vb \(在 Visual Basic 中\) 或 Entity1.cs 的快捷菜单 \(在 C\# 中\)，然后选择 ”删除“。  
  
5.  打开 Entity1Service.vb \(在 Visual Basic 中\) 或 Entity1Service.cs 的快捷菜单 \(在 C\# 中\)，然后选择 ”删除“。  
  
## 向模型添加实体  
 向模型添加实体。  您可以将实体从 Visual Studio 的“工具箱”加到 BDC 设计器上。  
  
#### 向模型添加实体  
  
1.  在菜单栏上，依次选择“查看”、“工具箱”。  
  
2.  在“工具箱”的“BusinessDataConnectivity”选项卡中，将“实体”加到 BDC 设计器上。  
  
     新实体随即显示在该设计器中。  Visual Studio 向名为 EntityService.vb（在 Visual Basic 中）或 EntityService.cs（在 C\# 中）的项目中添加一个文件。  
  
3.  在菜单栏上，选择“视图”，“属性" ,"窗口” 。  
  
4.  在“属性”窗口中，将“名称”属性设置为 Contact值。  
  
5.  在屏幕设计器中，打开实体的快捷菜单，选择“添加”，然后选择“Identifier”。  
  
     新标识符随即显示在该实体中。  
  
6.  在**“属性”**窗口中，将标识符的名称更改为“ContactID”。  
  
7.  在”类型名称“ 列表中，选择”System.Int32“ 。  
  
## 添加特定的 Finder 方法  
 若要启用 BDC 服务以显示特定联系人，必须添加特定的 Finder 方法。  当用户选择列表中的某一项，并单击功能区中的**“查看项”**按钮时，BDC 服务会调用特定的 Finder 方法。  
  
 使用**“BDC 方法详细信息”**窗口可以向联系人实体添加特定的 Finder 方法。  若要返回特定实体，请向该方法添加代码。  
  
#### 添加特定的 Finder 方法  
  
1.  在 BDC 设计器中，选择“联系人”实体。  
  
2.  在菜单栏上，依次选择 **视图**，**其他窗口**，**BDC 方法详细信息**。  
  
     打开“BDC 方法详细信息”窗口。  
  
3.  在 **添加方法** 列表中，选择 **创建特定的查找方法**。  
  
     Visual Studio 将以下元素添加到模型中。  这些元素将显示在**“BDC 方法详细信息”**窗口中。  
  
    -   一个名为“ReadItem”的方法。  
  
    -   该方法的输入参数。  
  
    -   该方法的返回参数。  
  
    -   每个参数的类型描述符。  
  
    -   该方法的一个方法实例。  
  
4.  在“BDC 方法详细信息”窗口中，打开出现的"联系"类型描述列表，然后选择 "编辑"。  
  
     该“BDC 资源管理器”打开并提供模型的分层视图。  
  
5.  在 ”属性“ 窗口，打开”类型名“  属性旁边列表，选择 ”当前项目“ 选项卡，然后选择 ”Contact“ 属性。  
  
6.  在 “BDC 资源管理器”，打开”联系“的快捷菜单，然后选择 “添加类型描述符”。  
  
     名为“TypeDescriptor1”的新类型描述符随即显示在“BDC 资源管理器”中。  
  
7.  在“属性”窗口中，将“名称”属性值设置为 **ContactID**。  
  
8.  打开属性旁边 ”TypeName“ 列表，然后选择”Int32“ 。  
  
9. 打开属性旁边 ”标识符“列表，然后选择 **ContactID**。  
  
10. 重复步骤 6 以为下列每个字段分别创建一个类型描述符。  
  
    |名称|类型名称|  
    |--------|----------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. 在 BDC 设计器的“联系人”实体上打开“ReadItem”方法。  
  
     联系人服务代码文件随即在代码编辑器中打开。  
  
12. 在 `ContactService` 类中，用下面的代码替换 `ReadItem` 方法。  这段代码执行下列任务：  
  
    -   从 AdventureWorks 数据库的联系人表中检索记录。  
  
    -   将 Contact 实体返回到 BDC 服务。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## 添加 Finder 方法  
 若要启用 BDC 服务以在列表中显示联系人，必须添加 Finder 方法。  使用**“BDC 方法详细信息”**窗口可以向联系人实体添加 Finder 方法。  若要向 BDC 服务返回实体集合，请向该方法添加代码。  
  
#### 添加 Finder 方法  
  
1.  在 BDC 设计器中，选择“联系人”实体。  
  
2.  在“BDC 方法详细信息”窗口中，折叠“ReadItem”节点。  
  
3.  在 ”添加方法“ 列表。”ReadList“ 方法下，选择 ”创建 Finder 方法“。  
  
     Visual Studio 将添加一个方法、一个返回参数和一个类型描述符。  
  
4.  在 BDC 设计器的“联系人”实体上，打开“ReadList”方法。  
  
     联系人服务代码文件随即在代码编辑器中打开。  
  
5.  在 `ContactService` 类中，用以下代码替换 `ReadList` 方法。  这段代码执行下列任务：  
  
    -   从 AdventureWorks 数据库的联系人表中检索数据。  
  
    -   将联系人实体列表返回到 BDC 服务。  
  
    > [!NOTE]  
    >  用您的服务器名称替换 `ServerName` 字段的值。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## 测试项目  
 运行项目时，SharePoint 网站将会打开，Visual Studio 将向业务数据连接服务添加您的模型。  在 SharePoint 中创建引用 Contact 实体的外部列表。  AdventureWorks 数据库中联系人的数据随即显示在该列表中。  
  
> [!NOTE]  
>  您可能必须修改 SharePoint 中的安全性设置，然后才能调试解决方案。有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
#### 测试项目  
  
1.  选择**“F5”**键。  
  
     SharePoint 网站将打开。  
  
2.  在"网站操作" 菜单中，选择 "更多选项" 命令。  
  
3.  在"创建" 页中，选择"外部列表" 模板，然后选择 "创建" 按钮。  
  
4.  将该自定义列表命名为“联系人”。  
  
5.  选择**“外部内容类型”**字段旁边的“浏览”按钮。  
  
6.  在“外部内容类型选取器”对话框中，选择“AdventureWorksContacts.BdcModel1.Contact”项，然后选择“创建”按钮。  
  
     SharePoint 随即创建包含 AdventureWorks 示例数据库中的联系人的外部列表。  
  
7.  若要测试特定的 Finder 方法，选择单击该列表中的某一联系人。  
  
8.  在功能区上，选择 ”项“ 选项卡，然后选择 ”查看项目“ 命令。  
  
     所选联系人的详细信息随即显示在窗体中。  
  
## 后续步骤  
 您可以通过以下主题了解有关如何在 SharePoint 中为 BDC 服务设计模型的更多内容：  
  
-   [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [如何：添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [如何：添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md).  
  
## 请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  