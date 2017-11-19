---
title: "演练： 从现有的 SharePoint 网站导入项目 |Microsoft 文档"
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
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 602615426a8aeca118f6faba65e21778136b0ce6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>演练：从现有的 SharePoint 网站导入项
  本演练演示如何从现有的 SharePoint 网站到导入项目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。  
  
 本演练演示了下列任务：  
  
-   通过添加自定义网站栏自定义 SharePoint 站点 (也称为*字段*。  
  
-   将 SharePoint 站点导入.wsp 文件。  
  
-   导入.wsp 文件到[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用.wsp 导入项目的 SharePoint。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的版本的[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="customizing-a-sharepoint-site"></a>自定义 SharePoint 站点  
 对于此示例，你将创建和自定义 SharePoint 子站点，通过向其添加新的网站栏并创建另一个子站点，以供稍后使用。 更高版本，将导出到.wsp 文件的第一个子站点，并通过.wsp 导入项目，然后导入第二个子站点的自定义网站栏。  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>若要创建和自定义 SharePoint 站点  
  
1.  打开 SharePoint 站点使用 Web 浏览器，如 http://*系统名称*/SitePages/Home.aspx。  
  
2.  通过打开创建子站点从主 SharePoint 网站**站点操作**菜单，然后选择**新站点**。  
  
3.  在站点的**创建**对话框框中，选择**空白站点**类型。  
  
4.  在**标题**框中，输入**站点列测试 1**; 在**URL 名称**框中，输入**columntest1**; 将其他设置保留其默认值值;然后选择**创建**按钮。  
  
5.  创建网站后，导航回主站点上，浏览器中 http://*系统名称*/SitePages/Home.aspx。  
  
6.  同样，通过打开创建空的子站点从主 SharePoint 网站**站点操作**菜单上，选择**新站点**，然后选择**空白站点**类型。  
  
7.  在**标题**框中，输入**站点列测试 2**; 在**URL 名称**框中，输入**columntest2**; 将其他设置保留其默认值值;然后选择**创建**按钮。  
  
8.  导航回第一个子站点，http://*系统名称*/columntest1/default.aspx。  
  
9. 上**站点操作**菜单上，选择**站点设置**以显示站点设置页。  
  
10. 在**库**部分中，选择**站点列**链接。  
  
11. 在顶部**网站栏库**页上，选择**创建**按钮。  
  
12. 在**列名**框中，输入**测试列**，保留的其他默认值，然后选择**确定**按钮。  
  
13. **测试列**列标题上出现后在自定义列下网站库中的列。  
  
## <a name="exporting-the-sharepoint-site"></a>导出 SharePoint 站点  
 接下来，获取一个包含 SharePoint 项和你想要导入到的元素的 SharePoint 安装程序 (.wsp) 文件您[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。 如果你还没有.wsp 文件，然后必须创建一个从现有的 SharePoint 网站。 对于本例，请将默认 SharePoint 站点导出到.wsp 文件。  
  
> [!IMPORTANT]  
>  如果收到运行时错误，执行以下过程，你必须能够访问 SharePoint 站点的系统上执行过程。  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>若要导出的现有的 SharePoint 站点  
  
1.  在 SharePoint 站点中，选择**站点设置**上**站点操作**选项卡以显示站点设置页。  
  
2.  在**站点操作**部分的站点设置页中，选择**保存为模板的站点**链接。  
  
3.  在**文件名**框中，输入**ExampleSite**，然后在**模板名称**框中，输入**站点示例**。  
  
4.  对于此示例中，将保留**内容包括**复选框为空。  
  
     如果选中此框中，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将所有列表和文档库和其内容保存到.wsp 文件。 尽管这可在某些情况下，它不是本示例所需。  
  
5.  该操作成功完成时，选择**解决方案库**链接可查看.wsp 文件。  
  
     若要查看解决方案库页上更高版本，打开**站点操作**菜单上，选择**站点设置**，选择**转到顶级网站设置**中链接**站点集合管理**部分，然后依次**解决方案**中链接**库**部分。  
  
6.  在解决方案库中，选择**ExampleSite**链接。  
  
7.  在**文件下载**对话框框中，选择**保存**按钮以保存您的本地系统上的文件，默认情况下，在 Downloads 文件夹。  
  
## <a name="importing-the-wsp-file"></a>导入.wsp 文件  
 现在，已.wsp 文件包含想要重用 （自定义网站栏测试列） 的项时，导入.wsp 文件来访问它。  
  
#### <a name="to-import-a-wsp-file"></a>若要导入.wsp 文件  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，在菜单栏上，选择**文件**，**新建**，**项目**以显示**新项目**对话框。 如果 IDE 设置为使用 Visual Basic 开发设置，在菜单栏上，选择**文件**，**新项目**。  
  
2.  展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**节点。  
  
3.  选择**导入 SharePoint 2010 解决方案包**中的模板**模板**窗格中，保留 WspImportProject1，作为项目的名称，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
4.  上**指定用于调试的站点和安全性级别**页上，输入[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]为前面创建第二个 SharePoint 个子站点。 你将添加新的自定义项，字段 http://*系统名称*/columntest2，到该子站点。  
  
5.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，保留为选择**部署为沙盒解决方案**。  
  
6.  在**指定新项目源**页上，浏览到其中先前保存.wsp 文件系统上的位置，然后选择**下一步**按钮。  
  
    > [!NOTE]  
    >  如果你选择**完成**将导入在此页上，.wsp 文件中的所有可用项的按钮。  
  
7.  在**选择要导入的项**框中，清除所有除列表中的复选框**测试列**，然后选择**完成**按钮。  
  
     由于该列表包含多个项，你可以选择 Ctrl + A 键以选择所有项在列表中，都选择空格键以清除所有复选框，然后选择仅复选框旁边**测试列**项。  
  
     导入操作完成后，一个名为的新项目后**WspImportProject1**创建包含名为的文件夹**字段**。 在此文件夹中为自定义网站栏**测试列**和 Elements.xml 其定义文件。  
  
## <a name="deploying-the-project"></a>部署项目  
 最后，部署**WspImportProject1**到第二个 SharePoint 子站点之前，若要查看自定义网站栏创建。  
  
#### <a name="to-deploy-the-project"></a>若要将项目部署  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，选择 F5 键以部署并运行.wsp 导入项目。  
  
2.  在 SharePoint 站点上，打开**站点操作**菜单，然后选择**站点设置**以显示站点设置页。  
  
3.  在**库**部分中，选择**站点列**链接。  
  
4.  向下滚动到**自定义列**部分。  
  
     请注意，从第一个 SharePoint 站点导入自定义网站栏显示在列表中。  
  
## <a name="see-also"></a>另请参阅  
 [从现有的 SharePoint 网站导入项](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  