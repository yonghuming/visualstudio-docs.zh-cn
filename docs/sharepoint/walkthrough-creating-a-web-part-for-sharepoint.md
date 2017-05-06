---
title: "演练：为 SharePoint 创建 Web 部件"
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
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 创建"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 设计"
  - "Web 部件 [Visual Studio 中的 SharePoint 开发], 开发"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 演练：为 SharePoint 创建 Web 部件
  通过 Web 部件，用户可以使用浏览器直接修改 SharePoint 网站页面的内容、外观和行为。  本演练演示如何使用 Visual Studio 2010 中的**“Web 部件”**项模板创建 Web 部件。  
  
 Web 部件在数据网格中显示员工。  用户可以指定包含员工数据的文件的位置，  还可以筛选数据网格，以便在列表中只显示作为经理的员工。  
  
 本演练阐释了以下任务：  
  
-   使用 Visual Studio 的**“Web 部件”**项模板创建 Web 部件。  
  
-   创建可供 Web 部件用户设置的属性。  该属性指定员工数据文件的位置。  
  
-   通过向 Web 部件控件集合添加控件来呈现 Web 部件中的内容。  
  
-   创建称为“谓词”的新菜单项，该菜单项在所呈现的 Web 部件的谓词菜单中显示。  用户可以使用谓词修改 Web 部件中显示的数据。  
  
-   在 SharePoint 中测试 Web 部件。  
  
    > [!NOTE]  
    >  以下说明中的某些 Visual Studio 用户界面元素在计算机上出现的名称或位置可能会不同。  您安装的 Visual Studio 版本以及使用的设置决定了这些元素。  有关详细信息，请参阅[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 系统必备  
 您需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。  有关详细信息，请参阅[开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]或 Visual Studio Application Lifecycle Management \(ALM\) 的某个版本。  
  
## 创建空 SharePoint 项目  
 首先，创建一个空 SharePoint 项目。  然后，使用**“Web 部件”**项模板向该项目添加 Web 部件。  
  
#### 创建空 SharePoint 项目  
  
1.  使用**“以管理员身份运行”**选项启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在菜单栏上，依次选择**“文件”**、**“新建”**和**“项目”**  
  
3.  在**“新建项目”**对话框中，展开要使用的语言下的**“SharePoint”**节点，然后选择**“2010”**节点。  
  
4.  在**“模板”**窗格中，选择**“SharePoint 2010 – 空项目”**项，然后选择**“确定”**按钮。  
  
     这将显示**“SharePoint 自定义向导”**。  使用此向导可以选择用于调试项目的站点以及解决方案的信任级别。  
  
5.  选择“部署为场解决方案”选项按钮，然后选择“完成”按钮以接受默认的本地 SharePoint 站点。  
  
## 向项目添加 Web 部件  
 向项目添加**“Web 部件”**项。  该**“Web 部件”**项将添加 Web 部件代码文件。  然后，向该 Web 部件代码文件添加代码，以呈现 Web 部件的内容。  
  
#### 向项目添加 Web 部件  
  
1.  在菜单栏上，依次选择“项目”、“添加新项”。  
  
2.  在**“添加新项”**对话框的**“已安装的模板”**窗格中，展开**“SharePoint”**节点，然后单击**“2010”**。  
  
3.  在SharePoint模板列表中，选择**“Web 部件”**模板，然后选择**“添加”**按钮。  
  
     **“Web 部件”**项随即显示在**“解决方案资源管理器”**中。  
  
## 呈现 Web 部件中的内容  
 通过将控件添加到 Web 部件类的控件集合中，可以指定要在 Web 部件中显示的控件。  
  
#### 呈现 Web 部件中的内容  
  
1.  在**“解决方案资源管理器”**中，开启 WebPart1.vb（在 Visual Basic 中）或 WebPart1.cs（在 C\# 中）。  
  
     Web 部件代码文件随即在代码编辑器中打开。  
  
2.  将以下语句添加到 Web 部件代码文件的顶部。  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  向 `WebPart1` 类添加以下代码。  此代码声明了以下字段：  
  
    -   用于在 Web 部件中显示员工的数据网格。  
  
    -   控件上显示的用于筛选数据网格的文本。  
  
    -   在数据网格无法显示数据时显示错误的标签。  
  
    -   包含员工数据文件路径的字符串。  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  向 `WebPart1` 类添加以下代码。  此代码将向 Web 部件添加一个名为 `DataFilePath` 的自定义属性。  自定义属性是用户可在 SharePoint 中设置的属性。  此属性获取和设置用于填充数据网格的 XML 数据文件的位置。  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  用下面的代码替换 `CreateChildControls` 方法。  这段代码执行下列任务：  
  
    -   添加在上一步骤中声明的数据网格和标签。  
  
    -   将数据网格绑定到包含员工数据的 XML 文件。  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  将以下方法添加到 `WebPart1` 类中。  这段代码执行下列任务：  
  
    -   创建一个谓词，该谓词显示在所呈现的 Web 部件的 Web 部件谓词菜单中。  
  
    -   处理当用户单击谓词菜单中的谓词时所引发的事件。  此代码筛选在数据网格中显示的员工列表。  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## 测试 Web 部件  
 在运行项目时，SharePoint 网站将打开。  Web 部件会自动添加到 SharePoint 中的 Web 部件库中。  您可以将 Web 部件添加到任何 Web 部件页。  
  
#### 测试 Web 部件  
  
1.  将以下 XML 粘贴到记事本文件中。  此 XML 文件包含将在 Web 部件中显示的示例数据。  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  在“记事本”的菜单栏上，依次选择**“文件”**、**“另存为”**。  
  
3.  在**“另存为”**对话框中的**“保存为类型”**下拉列表中，选择**“所有文件”**。  
  
4.  在**“文件名”**框中，键入“data.xml”。  
  
5.  单击**“浏览文件夹”**按钮并选择任意文件夹，然后单击**“保存”**按钮。  
  
6.  在 Visual Studio 中，按下 **F5** 键。  
  
     SharePoint 网站将打开。  
  
7.  在**“网站操作”**菜单上，单击**“更多选项”**  
  
8.  在**“创建”**页面上，将该页命名为**“SampleWebPartPage.aspx”**，然后选中“创建”按钮。  
  
9. 在**“新建 Web 部件页”**页上，将该页命名为**“SampleWebPartPage.aspx”**，然后选中**“创建”**按钮。  
  
     此时将显示 Web 部件页。  
  
10. 选择 Web 部件页上的任何区域。  
  
11. 在该页顶部单击**“插入”**选项卡，然后单击**“Web 部件”**。  
  
12. 在**“类别”**窗格中，依次单击**“自定义”**文件夹、**“WebPart1”**Web 部件和**“添加”**。  
  
     此时将在该页上显示 Web 部件。  
  
## 测试自定义属性  
 若要填充 Web 部件中显示的数据网格，请指定包含有关各个员工的数据的 XML 文件的路径。  
  
#### 测试自定义属性  
  
1.  单击”Web部件“右边的箭头，然后从显示的菜单中选中**“编辑Web部件”**。  
  
     包含 Web 部件属性的窗格将显示在该页的右侧。  
  
2.  在此窗格中，展开**“杂项”**节点，键入先前创建的 XML 文件的路径并单击**“应用”**，然后单击**“确定”**。  
  
     验证员工列表是否显示在 Web 部件中。  
  
## 测试 Web 部件谓词  
 通过单击显示在 Web 部件谓词菜单中的某一项来显示和隐藏不是经理的员工。  
  
#### 测试 Web 部件谓词  
  
1.  单击显示在“Web部件”右边的箭头，然后从显示的菜单中选中**“仅显示经理”**。  
  
     此时将在 Web 部件中仅显示作为经理的员工。  
  
2.  再次单击此箭头，然后从显示的菜单中选中**“显示所有员工”** 。  
  
     此时将在 Web 部件中显示所有员工。  
  
## 请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何：创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何：使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [演练：使用设计器为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  