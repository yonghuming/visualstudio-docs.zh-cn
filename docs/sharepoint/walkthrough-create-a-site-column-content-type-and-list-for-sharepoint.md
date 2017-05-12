---
title: "演练：创建 SharePoint 的网站栏、内容类型和列表"
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
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 内容类型"
  - "Visual Studio 中的 SharePoint 开发, 字段"
  - "Visual Studio 中的 SharePoint 开发, 列表定义"
  - "Visual Studio 中的 SharePoint 开发, 列表实例"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 演练：创建 SharePoint 的网站栏、内容类型和列表
  下面的过程演示如何创建自定义 SharePoint 站点列或 *字段*以及使用该网站栏的内容类型。  它还演示如何创建使用新内容类型的列表。  
  
 本演练包含以下任务：  
  
-   [创建自定义网站栏](#BKMK_CreatingCustSiteCols)。  
  
-   [创建自定义内容类型](#BKMK_CreateCustContType)。  
  
-   [创建列表](#BKMK_CreateList)。  
  
-   [创建列表](#BKMK_CreateList)。  
  
-   [测试应用程序](#BKMK_TestApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 系统必备  
 你需要以下组件来完成本演练：  
  
-   支持的 Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> 创建自定义网站栏  
 本例在医院生成托管患者的列表。  首先，必须在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建 SharePoint 项目和添加站点列，如下所示。  
  
#### 创建项目  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**“文件”**菜单上，选择**“新建”**，**“项目”**。  
  
2.  在**“新建项目”**对话框中，在**“Visual C\#”**或**“Visual Basic”**下，展开**“SharePoint”**节点，然后选择**“2010”**。  
  
3.  在 **模板** 窗格中，选择 **SharePoint 2010 项目** 模板，将项目名称改为 Clinic，然后选择 **确定** 按钮。  
  
     SharePoint 2010 项目模板是本示例包含网站栏和其他项目项之后添加的空项目。  
  
4.  在**“指定用于调试的网站和安全级别”**页上，输入要将新自定义字段项添加到的本地的 SharePointr 网站的 URL，或者使用默认位置 \(`http://<`*SystemName*`>/)`。  
  
5.  在**“此 SharePoint 解决方案的信任级别是什么?”**部分，使用默认值**“部署为沙盒解决方案”**。  
  
     有关沙盒解决方案与场解决方案的更多信息，请参见[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  选择**“完成”**按钮。  在 **解决方案资源管理器**应当将列出项目。  
  
#### 添加网站栏  
  
1.  添加新的网站栏。  为此，在**“解决方案资源管理器”**中，打开**Clinic**的快捷菜单，然后依次选择**“添加”**、**“新建项”**。  
  
2.  在**“添加新项”**对话框中选择**网站栏**，改变名称为Patient Name，然后选择**“添加”**按钮。  
  
3.  在网站栏的 Elements.xml 文件中，将 **类型** 设置为 **文本**，并将 **组** 设置为诊所网站栏。  完成后，网站栏的 Elements.xml 文件应类似于下面的示例。  
  
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
  
4.  使用同一过程，再添加两个网站列到项目：Patient ID \(类型 \=“整数”\) 和 Doctor Name \(类型 \=“Text”。\)  设置其组值为Clinic网站栏。  
  
##  <a name="BKMK_CreateCustContType"></a> 创建自定义内容类型  
 接下来，创建基于联系人内容类型的内容类型，包含了您在上一过程中创建的网站栏。  通过基于现有的内容类型，可以节省时间，因为在新的内容类型，基内容类型提供了多种列网站。  
  
#### 创建自定义内容类型  
  
1.  向项目中添加内容类型。  为此，在**“解决方案资源管理器”**中，选择项目节点。  
  
2.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在 **模板** 窗格中，选择 **内容类型** 模板，将名称更改为Patient Info，然后选择**添加** 按钮。  
  
     “SharePoint 自定义向导”打开。  
  
5.  在 **此内容类型应从哪一个基内容类型继承** 列表中，选择 **联系人** 作为新项目所基于的内容类型，然后选择 **完成** 按钮。  
  
     这样做可以访问其他可能有用网站栏的访问中联系人内容类型，以及以前定义的网站栏。  
  
6.  当内容类型设计器出现之后，在 **列** 选项卡，添加以前定义的三列站点 **Patient Name**、**Patient ID**和 **Doctor Name"**。  若要添加这些列，选择**显示名称**下，网站栏列表的第一个列表框 ，然后同时选择列表中的每一个站点列。  
  
    > [!TIP]  
    >  若要快速选择网站栏，通过输入列名称的前几个字母筛选列表。  
  
7.  除了三个自定义站点栏，从站点栏列表中添加 **注释** 站点栏。  
  
8.  选择 **Patient Name** 和 **Patient ID必填** 站点栏的复选框可使它们成为必填字段。  
  
9. 在 **内容类型** 选项卡，确保内容类型名称为 **Patient Info**，然后更改说明为Patient信息卡。  
  
10. 将 **组名称** 更改为Clinic内容类型，而将其他设置保留为其默认值。  
  
11. 在菜单栏上，依次选择 **文件**， **全部保存**，然后关闭内容类型设计器。  
  
##  <a name="BKMK_CreateList"></a> 创建列表  
 现在，生成使用新内容类型和站点栏的列表。  
  
#### 创建列表  
  
1.  向项目中添加列表。  为此，在**“解决方案资源管理器”**中，选择项目节点。  
  
2.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
3.  展开**“Visual C\#”**或**“Visual Basic”**下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在 **模板** 窗格中，选择 **列表** 模板，将名称更改为Patients，然后选择**添加** 按钮。  
  
5.  保留 **自定义列表依据** 设置为 **默认 \(空白\)**，然后选择 **完成** 按钮。  
  
6.  在设计器中，选择 **内容类型** 按钮列表显示 **内容类型设置** 对话框。  
  
7.  在内容类型列表，选择新行，选择**Patient Info**类型类型，然后选择 **确定** 按钮。  
  
     执行从 **Patient Info** 的内容类型添加所有站点栏导入到列表。  
  
8.  删除任何在网站栏的列表，除了以下操作：  
  
    -   病人的 ID  
  
    -   病人的名字  
  
    -   住宅电话  
  
    -   电子邮件  
  
    -   医生的名字  
  
    -   注释  
  
9. 在 **列显示名称**下，选择一个空行，添加自定义列表列，并命名为医院。  保留其数据类型为 **单行文本**。  
  
     自定义列表列只适用于此列表。  当您添加自定义列表列到列表时，新的列表内容类型，包括所有添加到列表的列，创建和设置为默认列表。  
  
    > [!TIP]  
    >  如果从站点栏列表中选择列，使用现有站点栏。  但是，如果您没有选择列表中的任何列而输入列的值，将创建自定义列表列，即使在列表中同名的列已经存在。  
  
     或者，而不是设置自定义列表的列的数据类型。**单行文本**，可以代替此列的数据类型为Lookup，并且其值从表或其他的列表中检索。  有关查找列的信息，请参见 [在 SharePoint 2010 的列表。](http://go.microsoft.com/fwlink/?LinkId=224994) 和 [查找关系和列表](http://go.microsoft.com/fwlink/?LinkID=224995)。  
  
10. 在 **Patient ID** 和 **Patient Name** 框旁边，选择 **必填** 复选框。  
  
11. 在 **视图** 选项卡，选择一个空行创建视图。  输入 Patient 的详细信息。  
  
     在 **视图** 选项卡，您可以指定一列要显示在 SharePoint 列表。  
  
12. 选择新的 **Patient的详细信息**行，然后选择 **设为默认值** 按钮。  
  
     新视图现在是列表的默认视图。  
  
13. 按以下顺序，添加下面的列到**选定的列** 列表：  
  
    -   病人的 ID  
  
    -   病人的名字  
  
    -   住宅电话  
  
    -   电子邮件  
  
    -   医生的名字  
  
    -   医院  
  
    -   注释  
  
14. 在 **属性** 列表中，选择 **排序和分组** 属性，然后选择省略号按钮 ![“省略号”图标](../sharepoint/media/ellipsisicon.png "“省略号”图标") 以显示 **排序和分组** 对话框。  
  
15. 在 **列名** 列表中，选择 **病人的名称**，，确保**排序**列设置为 **升序**，然后选择 **确定** 按钮。  
  
##  <a name="BKMK_TestApp"></a> 测试应用程序  
 既然自定义网站栏、内容类型和列表已准备就绪，请将它们部署到 SharePoint，然后运行应用程序测试它。  
  
#### 测试应用程序  
  
1.  在菜单栏上，依次选择**“文件”**、**“全部保存”**。  
  
2.  选择 F5 键运行应用程序。  
  
     应用程序编译，然后将其功能部署到 SharePoint并激活。  
  
3.  在运行速度快的导航栏中，选择 **患者** 链接显示 **患者** 列表。  
  
     列表中的列名必须与在 **视图** 选项卡访问 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]中的那些相匹配。  
  
4.  选择 **添加新项目** 链接创建一个患者的信息卡。  
  
5.  将信息输入到字段，然后选择 **保存** 按钮。  
  
     新记录出现在列表中。  
  
## 请参阅  
 [创建 SharePoint 的网站栏、内容类型和列表](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [如何：域创建自定义类型](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [内容类型](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columns](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  