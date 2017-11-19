---
title: "演练： 使用设计器为 SharePoint 创建 Web 部件 |Microsoft 文档"
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55da85b9740216cefe55911d79dab2c16b035695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>演练：使用设计器为 SharePoint 创建 Web 部件
  如果你创建 web 部件的 SharePoint 站点，你的用户可以直接修改内容、 外观和行为的该站点中的页通过使用浏览器。 本演练演示如何通过使用 SharePoint 直观地创建 web 部件**可视 Web 部件**中的项目模板[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
 你将创建的 web 部件显示站点上的每月的日历视图和复选框为每个日历列表。 用户可以指定哪些日历列出要包含在每月的日历视图中通过选择复选框。  
  
 本演练阐释了以下任务：  
  
-   通过使用创建 web 部件**可视 Web 部件**项目模板。  
  
-   通过使用 Visual Studio 中 Visual Web Developer 设计器设计 web 部件。  
  
-   添加代码以处理上 web 部件控件的事件。  
  
-   在 SharePoint 中测试 web 部件。  
  
    > [!NOTE]  
    >  你的计算机可能出现以下说明中的不同名称或 for Visual Studio 用户界面的某些元素的位置。 这些元素取决于你所使用的 Visual Studio 版本和你所使用的设置。 请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   受支持的 Windows 和 SharePoint 的版本。 请参阅[开发 SharePoint 解决方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]或更高版本。  
  
## <a name="creating-a-web-part-project"></a>创建 web 部件项目  
 首先，通过使用创建 web 部件项目**可视 Web 部件**项目模板。  
  
#### <a name="to-create-a-visual-web-part-project"></a>若要创建的可视 Web 部件项目  
  
1.  启动[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用**以管理员身份运行**选项。  
  
2.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
     此时将出现 “新建项目” 对话框。  
  
3.  在**新项目**对话框中下, **Visual C#**或**Visual Basic**，展开**Office/SharePoint**，然后选择**SharePoint 解决方案**类别。  
  
4.  在模板列表中，选择**SharePoint 2013 的可视 Web 部件**模板，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。 通过使用此向导，你可以指定将用于调试项目和解决方案的信任级别的站点。  
  
5.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，选择**部署为场解决方案**选项按钮。  
  
6.  选择**完成**按钮以接受默认的本地 SharePoint 站点。  
  
## <a name="designing-the-web-part"></a>设计 web 部件  
 通过添加从控件设计 web 部件**工具箱**到 Visual Web Developer 设计器图面。  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>若要设计 web 部件的布局  
  
1.  在 Visual Web Developer 设计器中，选择**设计**选项卡以切换到设计视图。  
  
2.  在菜单栏上，依次选择“视图”、“工具箱”。  
  
3.  在**标准**节点**工具箱**，选择**按**控制，，然后执行以下步骤之一：  
  
    -   打开的快捷菜单**按**控件中，选择**复制**，在设计器中，打开第一个行的快捷菜单，然后选择**粘贴**。  
  
    -   拖动**按**控件从**工具箱**，并将该控件连接到设计器中的第一行。  
  
4.  重复上一步中，但将一个按钮移到下一行的设计器。  
  
5.  在设计器中，选择**Button1**按钮。  
  
6.  在菜单栏上，选择**视图**，**属性窗口**。  
  
     **属性**窗口随即打开。  
  
7.  在**文本**的按钮，属性输入**更新**。  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>处理的 web 部件控件的事件  
 添加代码，使用户能够将日历添加到母版日历视图。  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>若要处理上 web 部件控件的事件  
  
1.  执行下面的某一组步骤：  
  
    -   在设计器中，双击**更新**按钮。  
  
    -   在**属性**窗口**更新**按钮，选择**事件**按钮。 在**单击**属性，输入**Button1_Click**，然后选择 Enter 键。  
  
     用户控件的代码文件将在代码编辑器中打开和`Button1_Click`事件处理程序将显示。 更高版本，你将添加到此事件处理程序的代码。  
  
2.  用户控件的代码文件的顶部添加以下语句。  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  添加以下代码的行`VisualWebPart1`类。 此代码声明的每月的日历视图控件。  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  替换`Page_Load`方法`VisualWebPart1`类替换为以下代码。 这段代码执行下列任务：  
  
    -   将每月的日历视图添加到用户控件。  
  
    -   在站点上添加复选框为每个日历列表。  
  
    -   日历视图中指定用于每种类型的显示项的模板。  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  替换`Button1_Click`方法`VisualWebPart1`类替换为以下代码。 此代码将从所选的每个日历项添加到母版日历视图中。  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>测试 web 部件  
 运行项目时，会打开 SharePoint 站点。 Web 部件自动添加到在 SharePoint Web 部件库中。 若要测试此项目，将执行以下任务：  
  
-   将事件添加到每两个单独的日历的列表。  
  
-   将 web 部件添加到 web 部件页。  
  
-   指定要包含在每月的日历视图中的列表。  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>若要将事件添加到网站上的日历列表  
  
1.  在 Visual Studio 中，选择 F5 键。  
  
     将打开 SharePoint 站点，与[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]快速启动栏显示在此页。  
  
2.  在快速启动栏上，在**列出**，选择**日历**链接。  
  
     **日历**页将出现。  
  
     如果你没有日历链接显示在快速启动栏上，选择**站点内容**链接。 如果站点内容页不会显示**日历**项，创建一个。  
  
3.  在日历页上，选择一天，然后选择**添加**在选定的日期，以添加事件的链接。  
  
4.  在**标题**框中，输入**中的默认日历事件**，然后选择**保存**按钮。  
  
5.  选择**站点内容**链接，然后再选择**添加应用程序**磁贴。  
  
6.  上**创建**页上，选择**日历**键入，日历，命名，然后选择**创建**按钮。  
  
7.  将事件添加到新的日历，将事件**自定义日历中的事件**，然后选择**保存**按钮。  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>若要将 web 部件添加到 web 部件页  
  
1.  上**站点内容**页上，打开**网站页**文件夹。  
  
2.  在功能区中，选择**文件**选项卡上，打开**新文档**菜单，然后选择**Web 部件页**命令。  
  
3.  上**新建 Web 部件页**页上，将该页命名为**SampleWebPartPage.aspx**，然后选择**创建**按钮。  
  
     Web 部件页将显示。  
  
4.  在 web 部件页的顶部区域中，选择**插入**选项卡上，然后选择**Web 部件**按钮。  
  
5.  选择**自定义**文件夹中，选择**VisualWebPart1** web 部件，，然后选择**添加**按钮。  
  
     Web 部件显示在此页。 以下控件显示 web 部件：  
  
    -   每月的日历视图。  
  
    -   **更新**按钮。  
  
    -   A**日历**复选框。  
  
    -   A**自定义日历**复选框。  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>可以指定列表以包含在每月的日历视图  
  
1.  在 web 部件中，指定你想要包括在每月的日历视图中，然后选择的日历**更新**按钮。  
  
     从你指定的所有日历事件出现在每月的日历视图。  
  
## <a name="see-also"></a>另请参阅  
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [如何： 创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [如何： 使用设计器创建 SharePoint Web 部件](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [演练：为 SharePoint 创建 Web 部件](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  