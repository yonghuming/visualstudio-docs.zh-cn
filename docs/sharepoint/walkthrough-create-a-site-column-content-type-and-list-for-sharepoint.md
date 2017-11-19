---
title: "演练： 创建网站栏、 内容类型和 SharePoint 列表 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d6007dee14f89f875c66009f048b47579e97028b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>演练：创建 SharePoint 的网站栏、内容类型和列表
  以下过程演示如何创建自定义 SharePoint 网站栏 — 或*字段*-以及所使用的站点列的内容类型。 它还演示如何创建使用新的内容类型的列表。  
  
 本演练包含以下任务：  
  
-   [创建自定义网站栏](#BKMK_CreatingCustSiteCols)。  
  
-   [创建自定义的内容类型](#BKMK_CreateCustContType)。  
  
-   [创建列表](#BKMK_CreateList)。  
  
-   [创建列表](#BKMK_CreateList)。  
  
-   [测试应用程序](#BKMK_TestApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   受支持的 Windows 和 SharePoint 的版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>创建自定义网站栏  
 此示例创建用于管理在医院患者列表。 首先，必须创建中的 SharePoint 项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]并将站点列添加到它，，如下所示。  
  
#### <a name="to-create-the-project"></a>创建项目  
  
1.  上[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**文件**菜单上，选择**新建**，**项目**。  
  
2.  在**新项目**对话框中下, **Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**。  
  
3.  在**模板**窗格中，选择**SharePoint 2010 项目**，更改到项目的名称**Clinic**，然后选择**确定**按钮。  
  
     SharePoint 2010 项目模板是一个空的项目，在此示例中用来包含网站栏和之后添加其他项目项。  
  
4.  上**指定用于调试的站点和安全性级别**页上，输入你想要添加的新的自定义字段项的本地 SharePoint 站点的 URL 或使用默认位置 (`http://<`*系统名称*`>/)`.  
  
5.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，使用默认值**部署为沙盒解决方案**。  
  
     有关沙盒的详细信息和场解决方案，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  选择**完成**按钮。 项目现在应列入**解决方案资源管理器**。  
  
#### <a name="to-add-site-columns"></a>若要添加站点列  
  
1.  添加新的站点列。 为此，请在**解决方案资源管理器**，打开快捷菜单**Clinic**，然后选择**添加**，**新项**。  
  
2.  在**添加新项**对话框框中，选择**网站栏**，名称更改为**患者名称**，然后选择**添加**按钮。  
  
3.  在网站栏的 Elements.xml 文件中，保留**类型**将设置为**文本**，并更改**组**将设置为**Clinic 网站栏**。 完成后，网站栏的 Elements.xml 文件应类似下面的示例。  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  使用相同的过程中，向项目添加两个详细的网站栏：**患者 ID** (类型 ="Integer") 和**Doctor 名称**(类型 ="Text")。 将其组值设置为**Clinic 网站栏**。  
  
##  <a name="BKMK_CreateCustContType"></a>创建自定义的内容类型  
 接下来，创建的内容类型-基于联系人内容类型，包括你在前面的过程中创建网站栏。 通过使基于现有的内容类型的内容类型，可以节省时间，因为基的内容类型提供多个站点列在新的内容类型中使用。  
  
#### <a name="to-create-a-custom-content-type"></a>若要创建自定义内容类型  
  
1.  向项目添加内容类型。 为此，请在**解决方案资源管理器**，选择项目节点  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在**模板**窗格中，选择**内容类型**模板，名称更改为**患者信息**，然后选择**添加**按钮。  
  
     **SharePoint 自定义向导**打开。  
  
5.  在**内容的基类型应此内容类型继承自**列表中，选择**联系人**上要基于新的内容类型，然后选择的内容类型为**完成**按钮。  
  
     执行此操作中的其他可能有用的站点列联系人内容类型，除了以前定义的网站栏使你可以访问。  
  
6.  在内容类型后设计器随即出现，在**列**选项卡上，添加三个站点以前定义的列：**患者名称**，**患者 ID**，和**Doctor 名称**。 若要添加这些列，选择第一个列表框中，在下的站点列列表**显示名称**，然后在一个列表中选择每个站点列，一次。  
  
    > [!TIP]  
    >  若要更快地选择网站栏，请通过输入列的名称的第一个几个字母筛选列表。  
  
7.  除了三个自定义网站栏中，添加**注释**站点从站点列列表的列。  
  
8.  选择**必需**复选框**患者名称**和**患者 ID**网站栏，以使它们所需字段。  
  
9. 上**内容类型**选项卡上，请确保内容类型名称是**患者信息**，然后将更改到说明**患者信息卡**。  
  
10. 更改**组名称**到**Clinic 内容类型**，并将其他设置保留为其默认值。  
  
11. 在菜单栏上，选择**文件**，**保存所有**，然后关闭设计器中内容类型。  
  
##  <a name="BKMK_CreateList"></a>创建列表  
 现在，创建使用新的内容类型和站点列的列表。  
  
#### <a name="to-create-a-list"></a>若要创建的列表  
  
1.  将列表添加到项目。 为此，请在**解决方案资源管理器**，选择项目节点。  
  
2.  在菜单栏上，选择**项目**，**添加新项**。  
  
3.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**节点。  
  
4.  在**模板**窗格中，选择**列表**模板，名称更改为**患者**，然后选择**添加**按钮。  
  
5.  保留**自定义列表基于**将设置为**默认 （空）**，然后选择**完成**按钮。  
  
6.  在列表设计器中，选择**内容类型**按钮以显示**内容类型设置**对话框。  
  
7.  选择新行中，选择**患者信息**内容类型列表中的内容类型，然后选择**确定**按钮。  
  
     执行此操作将添加的所有站点列从**患者信息**内容到列表的类型。  
  
8.  删除所有站点中的列的列表，以下除外：  
  
    -   患者 ID  
  
    -   患者名称  
  
    -   住宅电话  
  
    -   电子邮件  
  
    -   Doctor 名称  
  
    -   注释  
  
9. 下**列显示名称**、 选择一个空行，添加自定义列表列时，并将其命名**医院**。 保持其数据类型作为**单个文本行**。  
  
     自定义的列表列仅适用于此列表。 当将自定义的列表列添加到列表中时，新列表的内容类型，包括添加到列表中，所有列创建，并将设置为默认列表。  
  
    > [!TIP]  
    >  如果从站点列的列表中选择某一列，则使用现有的网站列。 但是，如果输入列的名称值不在列表中选择任何列的情况下，自定义列表创建列后，即使在列表中已存在具有相同名称的列。  
  
     （可选） 而设置的自定义列表列的数据类型不是**单个文本行**，则改为可通过以下方式设置此列的数据类型为查找，并且将从表或另一个列表中检索其值。 有关查找列的信息，请参阅[在 SharePoint 2010 中的列表关系](http://go.microsoft.com/fwlink/?LinkId=224994)和[查找和列表关系](http://go.microsoft.com/fwlink/?LinkID=224995)。  
  
10. 旁边**患者 ID**和**患者名称**框中，选择**所需**复选框。  
  
11. 上**视图**选项卡上，选择一个空行以创建视图。 输入**患者详细信息**。  
  
     上**视图**选项卡上，你可以指定你想要在 SharePoint 列表中显示的列。  
  
12. 选择新**患者详细信息**行，，然后选择**设为默认值**按钮。  
  
     新视图现在是列表的默认视图。  
  
13. 添加到下列**选定的列**按以下顺序的列表：  
  
    -   患者 ID  
  
    -   患者名称  
  
    -   住宅电话  
  
    -   电子邮件  
  
    -   Doctor 名称  
  
    -   医院  
  
    -   注释  
  
14. 在**属性**列表中，选择**排序和分组**属性，然后选择省略号按钮![省略号图标](../sharepoint/media/ellipsisicon.gif "省略号图标")以显示**排序和分组**对话框。  
  
15. 在**列名**列表中，选择**患者名称**，请确保**排序**列设置为**升序**，然后选择**确定**按钮。  
  
##  <a name="BKMK_TestApp"></a>测试应用程序  
 现在，自定义网站栏、 内容类型和列表准备就绪后，将它们部署到 SharePoint，并运行应用程序对其进行测试。  
  
#### <a name="to-test-the-application"></a>测试应用程序  
  
1.  在菜单栏上，依次选择“文件”、“全部保存”。  
  
2.  选择 F5 键运行应用程序。  
  
     编译，应用程序，然后部署到 SharePoint 并激活其功能。  
  
3.  在快速导航栏中，选择**患者**链接以显示**患者**列表。  
  
     列表中的列名称应匹配那些在输入**视图**选项卡中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
4.  选择**添加新项**链接，创建患者信息卡。  
  
5.  在字段中输入信息，然后选择**保存**按钮。  
  
     新的记录将出现在列表中。  
  
## <a name="see-also"></a>另请参阅  
 [为 SharePoint 创建网站栏、 内容类型和列表](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [如何： 创建自定义字段类型](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [内容类型](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [列](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  