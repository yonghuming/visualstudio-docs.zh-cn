---
title: "演练： 使用业务数据在 SharePoint 中创建外部列表 |Microsoft 文档"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: babb8456593ba953982390f048960449069ca6fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>演练：使用业务数据在 SharePoint 中创建外部列表
  业务数据连接 (BDC) 服务使 SharePoint，以显示从后端服务器应用程序、 Web 服务和数据库的业务数据。  
  
 本演练演示了如何创建示例数据库中返回的联系人信息 BDC 服务的型号。 然后，您将使用此模型在 SharePoint 中创建外部列表。  
  
 本演练阐释了以下任务：  
  
-   创建项目。  
  
-   将实体添加到模型。  
  
-   添加 finder 方法。  
  
-   添加特定的 finder 方法。  
  
-   测试项目。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   受支持的 Windows 和 SharePoint 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] 或 [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]。  
  
-   对 AdventureWorks 示例数据库的访问。 有关如何安装 AdventureWorks 数据库的详细信息，请参阅[SQL Server 示例数据库](http://go.microsoft.com/fwlink/?LinkID=117483)。  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>创建一个包含 BDC 模型的项目  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>创建一个包含 BDC 模型的项目  
  
1.  在菜单栏上 Visual Studio 中，选择**文件**，**新建**，**项目**。  
  
     **“新建项目”** 对话框随即打开。  
  
2.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**项。  
  
3.  在**模板**窗格中，选择**SharePoint 2010 项目**，命名该项目**命名为 AdventureWorksTest**，然后选择**确定**按钮.  
  
     **SharePoint 自定义向导**显示。 在此向导中，你可以指定将用于调试项目和解决方案的信任级别设置的站点。  
  
4.  选择**部署为场解决方案**选项按钮以设置信任级别。  
  
5.  选择**完成**按钮以接受默认的本地 SharePoint 站点。  
  
6.  在**解决方案资源管理器**，选择 SharePoint 项目节点。  
  
7.  在菜单栏上，选择**项目**，**添加新项**。  
  
     此时将打开“添加新项”对话框。  
  
8.  在**模板**窗格中，选择**业务数据连接模型 （仅场解决方案）**，命名该项目**命名为 AdventureWorksContacts**，然后选择**添加**按钮。  
  
## <a name="adding-data-access-classes-to-the-project"></a>添加到项目的数据访问类  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>若要向项目中添加数据访问类  
  
1.  在菜单栏上，选择**工具**，**连接到数据库**。  
  
     **添加连接**对话框随即打开。  
  
2.  添加到 SQL Server AdventureWorks 示例数据库的连接。  
  
     有关详细信息，请参阅[添加/修改连接 (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3)。  
  
3.  在 **“解决方案资源管理器”**中，选择项目节点。  
  
4.  在菜单栏上，选择**项目**，**添加新项**。  
  
5.  在**已安装的模板**窗格中，选择**数据**节点。  
  
6.  在**模板**窗格中，选择**LINQ to SQL 类**。  
  
7.  在**名称**框中，指定**AdventureWorks**，然后选择**添加**按钮。  
  
     .dbml 文件会添加到项目中，对象关系设计器（O/R 设计器）将打开。  
  
8.  在菜单栏上，选择**视图**，**服务器资源管理器**。  
  
9. 在**服务器资源管理器**，展开表示 AdventureWorks 示例数据库的节点，然后展开**表**节点。  
  
10. 添加**Contact (Person)**拖动到 O/R 设计器的表。  
  
     一个实体类将创建并显示在设计图面上。 该实体类的属性映射到 Contact (Person) 表中的列。  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>默认实体移除 BDC 模型  
 **业务数据连接模型**项目添加到模型名为 Entity1 的默认实体。 删除此实体。 稍后，你将添加新实体。 从一个空模型可减少所需完成本演练的步骤数。  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>若要从模型中删除默认实体  
  
1.  在**解决方案资源管理器**，展开**BdcModel1**节点，然后打开 BdcModel1.bdcm 文件。  
  
2.  在 BDC 设计器中打开该业务数据连接模型文件。  
  
3.  在设计器中，打开快捷菜单**Entity1**，然后选择**删除**。  
  
4.  在**解决方案资源管理器**，打开 Entity1.vb （在 Visual Basic 中) 或 Entity1.cs （在 C# 中) 的快捷菜单，然后选择**删除**。  
  
5.  打开 Entity1Service.vb （在 Visual Basic 中) 或 Entity1Service.cs （在 C# 中) 的快捷菜单，然后选择**删除**。  
  
## <a name="adding-an-entity-to-the-model"></a>将实体添加到模型  
 将实体添加到模型。 可以从 Visual Studio 中添加实体**工具箱**拖动到 BDC 设计器。  
  
#### <a name="to-add-an-entity-to-the-model"></a>若要将实体添加到模型  
  
1.  在菜单栏上，依次选择“视图”、“工具箱”。  
  
2.  上**BusinessDataConnectivity**选项卡**工具箱**，添加**实体**拖动到 BDC 设计器。  
  
     在设计器上将显示新的实体。 Visual Studio 将添加到项目中是名为的 EntityService.vb （在 Visual Basic) 或 EntityService.cs （在 C# 中) 的文件。  
  
3.  在菜单栏上，选择**视图**，**属性**，**窗口**。  
  
4.  在**属性**窗口中，设置**名称**属性值设置为**联系人**。  
  
5.  在设计器中，打开实体的快捷菜单，选择**添加**，然后选择**标识符**。  
  
     一个新的标识符将出现在该实体。  
  
6.  在**属性**窗口中，更改到的标识符名称**ContactID**。  
  
7.  在**类型名称**列表中，选择**System.Int32**。  
  
## <a name="adding-a-specific-finder-method"></a>添加特定的 Finder 方法  
 若要启用 BDC 服务，以显示特定联系人，必须添加特定的 Finder 方法。 当用户选择列表中的项，然后选择时，BDC 服务会调用特定的 Finder 方法**视图项**功能区上的按钮。  
  
 通过将特定的 Finder 方法添加到联系人实体**BDC 方法详细信息**窗口。 若要返回的特定实体，请将代码添加到该方法。  
  
#### <a name="to-add-a-specific-finder-method"></a>若要添加特定的 Finder 方法  
  
1.  在 BDC 设计器中，选择**联系人**实体。  
  
2.  在菜单栏上，选择**视图**，**其他窗口**， **BDC 方法详细信息**。  
  
     “BDC 方法详细信息”窗口将打开。  
  
3.  在**添加一个方法**列表中，选择**创建特定的 Finder 方法**。  
  
     Visual Studio 将以下元素添加到模型。 这些元素出现在**BDC 方法详细信息**窗口。  
  
    -   一个名为 ReadItem 的方法。  
  
    -   输入的参数的方法。  
  
    -   返回参数的方法。  
  
    -   每个参数类型描述符。  
  
    -   方法实例的方法。  
  
4.  在**BDC 方法详细信息**窗口中，打开列表为显示**联系人**类型描述符，，然后选择**编辑**。  
  
     **BDC 资源管理器**将打开，并提供模型的分层视图。  
  
5.  在**属性**窗口中，打开列表旁边**TypeName**属性，选择**当前项目**选项卡上，然后选择**联系人**属性。  
  
6.  在**BDC 资源管理器**，打开快捷菜单**联系人**，然后选择**添加类型描述符**。  
  
     名为的新类型描述符**TypeDescriptor1**出现在**BDC 资源管理器**。  
  
7.  在**属性**窗口中，设置**名称**属性值设置为**ContactID**。  
  
8.  打开列表旁边**TypeName**属性，然后选择**Int32**。  
  
9. 打开列表旁边**标识符**属性，然后选择**ContactID**。  
  
10. 重复步骤 6 以创建针对每个以下字段的类型描述符。  
  
    |名称|类型名称|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |电话|System.String|  
    |电子邮件地址|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. 在 BDC 设计器上**联系人**实体中，打开**ReadItem**方法。  
  
     联系人服务代码文件将在代码编辑器中打开。  
  
12. 在`ContactService`类中，替换`ReadItem`方法替换为以下代码。 这段代码执行下列任务：  
  
    -   从 Contact 表的 AdventureWorks 数据库中检索一条记录。  
  
    -   返回到 BDC 服务 Contact 实体。  
  
    > [!NOTE]  
    >  值替换`ServerName`字段替换为你的服务器的名称。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>添加 Finder 方法  
 若要启用 BDC 服务，以显示联系人列表中，必须添加 Finder 方法。 通过将 Finder 方法添加到联系人实体**BDC 方法详细信息**窗口。 若要返回到 BDC 服务实体的集合，请将代码添加到该方法。  
  
#### <a name="to-add-a-finder-method"></a>若要添加 Finder 方法  
  
1.  在 BDC 设计器中，选择**联系人**实体。  
  
2.  在**BDC 方法详细信息**窗口中，折叠**ReadItem**节点。  
  
3.  在**添加一个方法**列表下**ReadList**方法中，选择**创建 Finder 方法**。  
  
     Visual Studio 添加方法、 返回的参数，并将类型描述符。  
  
4.  在 BDC 设计器上**联系人**实体中，打开**ReadList**方法。  
  
     联系人服务代码文件随即在代码编辑器中打开。  
  
5.  在`ContactService`类中，替换`ReadList`方法替换为以下代码。 这段代码执行下列任务：  
  
    -   从 AdventureWorks 数据库的联系人表中检索数据。  
  
    -   返回到 BDC 服务联系人实体的列表。  
  
    > [!NOTE]  
    >  值替换`ServerName`字段替换为你的服务器的名称。  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>测试项目  
 运行项目时，SharePoint 站点会打开，Visual Studio 将你的模型添加到业务数据连接服务。 在引用的联系人实体的 SharePoint 中创建外部列表。 列表中显示的 AdventureWorks 数据库中的联系人数据。  
  
> [!NOTE]  
>  你可能必须修改你在 SharePoint 中的安全设置，你可以调试你的解决方案之前。  有关详细信息，请参阅[设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
#### <a name="to-test-the-project"></a>测试项目  
  
1.  选择**F5**密钥。  
  
     打开 SharePoint 站点。  
  
2.  上**站点操作**菜单上，选择**更多选项**命令。  
  
3.  上**创建**页上，选择**外部列表**模板，然后选择**创建**按钮。  
  
4.  将自定义列表命名为**联系人**。  
  
5.  选择浏览按钮旁边**外部内容类型**字段。  
  
6.  在**外部内容类型选取器**对话框框中，选择**AdventureWorksContacts.BdcModel1.Contact**项，然后依次**创建**按钮。  
  
     SharePoint 随即创建包含 AdventureWorks 示例数据库中的联系人的外部列表。  
  
7.  若要测试特定的 Finder 方法，请在列表中选择联系人。  
  
8.  在功能区中，选择**项**选项卡上，然后选择**视图项**命令。  
  
     所选联系人的详细信息随即显示在窗体中。  
  
## <a name="next-steps"></a>后续步骤  
 你可以了解有关如何设计为在 SharePoint 中从下面这些主题的 BDC 服务模型的详细信息：  
  
-   [如何： 添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)。  
  
-   [如何： 添加 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)。  
  
-   [如何： 添加 Deleter 方法](../sharepoint/how-to-add-a-deleter-method.md)。  
  
## <a name="see-also"></a>另请参阅  
 [设计业务数据连接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC 模型设计工具概述](../sharepoint/bdc-model-design-tools-overview.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  